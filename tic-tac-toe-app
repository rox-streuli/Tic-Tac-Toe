# TIC-TAC-TOE
# #
# Estimated time
# 30-45 minutes
#
# Level of difficulty
# Hard
#
# Objectives
# Learn practical skills related to:
#
#    dealing with the grid geometry manager,

#    defining and using callbacks,

#    identifying and servicing GUI events.

# Scenario
# Write a simple GUI program which pretends to play tic-tac-toe with
# the user. Don't be afraid, we don't want you to implement artificial
# intelligence algorithms. You can do it, if you want, but we prefer
# to concentrate on the user interface issues. If you really want to
# create an actual competitor, do it on your own.
#
# This is what the game you are about to write looks like
# (the beginning and sample end of the game):
#
# To make your task a bit easier, let's simplify the game a bit.
# Here are our assumptions:.
#
#    the computer (i.e., your program) plays 'X', and Xes are always red,

#    the user (e.g., you) plays 'O', and Os are always green,

#    the board consists of 9 tiles, and the tile role is played by a button,

#   the first move belongs to the computer - it always puts its first 'X'
#   in the middle of the board,

#   the user enters her/his move by clicking the chosen tile (clicking
#   the tiles which are not free is ineffective)

#   the program checks if the game over conditions are met, and if the
#   game is over, a message box is displayed announcing the winner,

#   otherwise the computer responds with its move and the check is repeated,

#    use random to generate the computer's moves.

import tkinter as tk
from tkinter import messagebox
import random


def wins(win):
    for x in range(3):
        if win == board[x][0]["text"] == board[x][1]["text"] == board[x][2]["text"]:
            return message(win)
        if win == board[0][x]["text"] == board[1][x]["text"] == board[2][x]["text"]:
            return message(win)
    if win == board[0][0]["text"] == board[1][1]["text"] == board[2][2]["text"]:
        return message(win)
    if win == board[0][2]["text"] == board[1][1]["text"] == board[2][0]["text"]:
        return message(win)
    return None


def message(win):
    winner = ""
    if win == "O":
        winner = "You win!"
    elif win == "X":
        winner = "I win!"
    else:
        if win == "Draw":
            winner = "Draw"
    messagebox.showinfo(title="Game Over", message=winner)
    window.destroy()


def free():
    free_cells = []
    for c in range(3):
        for r in range(3):
            if board[r][c]["text"] == "":
                free_cells.append((r, c))
    return free_cells


def machine_move():
    global your_turn
    free_now = free()
    if len(free_now) == 0:
        message("draw")
    now = free_now[random.randrange(0, len(free_now))]
    print(now)
    butt = board[now[0]][now[1]]
    butt["text"] = "X"
    butt["fg"] = "red"
    butt["bg"] = "white"
    wins("X")
    your_turn = True


def move(event):
    global your_turn
    cell_selected = event.widget
    if your_turn:
        if cell_selected["text"] == "":
            cell_selected["text"] = "O"
            cell_selected["fg"] = "green"
            cell_selected["bg"] = "white"
            wins("O")
            your_turn = False
            machine_move()


window = tk.Tk()
window.title("TicTacToe")
window.minsize(250, 250)

board = [[None for c in range(3)] for r in range(3)]
print(board)
# None
# The sole value of the type NoneType. None is frequently used to represent
# the absence of a value, as when default arguments are not passed to a
# function. Assignments to None are illegal and raise a SyntaxError.

# THE GAME WORKS BUT... gives this exception when game is over
# Exception in Tkinter callback
# Traceback (most recent call last):
#   File "C:\...__init__.py", line 1883, in __call__
#     return self.func(*args)
#   File "C:/...6_lab.py", line 111, in move
#     machine_move()
#   File "C:....6_lab.py", line 91, in machine_move
#     free_now = free()
#   File "C:/....1.1.6_lab.py", line 81, in free
#     if board[r][c]["text"] == "":
#   File "C:\Us....__init__.py", line 1643, in cget
#     return self.tk.call(self._w, 'cget', '-' + key)
# _tkinter.TclError: invalid command name ".!button"
#
# Process finished with exit code 0

for row in range(3):
    for col in range(3):
        if row == 1 and col == 1:
            cell = tk.Button(window, text="X", fg="red",
                             font=("Arial", "32"), width=3)
            cell.grid(row=1, column=1)
        else:
            cell = tk.Button(window, text="", bg="grey",
                             font=("Arial", "32"), width=3)
            cell.grid(row=row, column=col)
        cell.bind("<Button-1>", move)
        board[row][col] = cell

your_turn = True

window.mainloop()
