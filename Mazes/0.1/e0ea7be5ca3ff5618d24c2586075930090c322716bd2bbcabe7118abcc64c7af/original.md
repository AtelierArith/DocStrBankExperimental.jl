`draw_ans(M::Maze)` draws the maze `M` and the solution (as a dotted red line) from the start (upper left) to the end (lower right).

To draw a different path (solution) use `draw(M,s,t)` where `s` and `t` are integer 2-tuples. Note that squares in the maze are indexed like a matrix, so `(2,3)` refers to the cell in row 2, column 3.
