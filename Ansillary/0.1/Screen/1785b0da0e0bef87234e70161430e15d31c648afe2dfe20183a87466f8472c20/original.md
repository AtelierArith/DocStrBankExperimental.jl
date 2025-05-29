This module deals with controlling what is displayed on the screen.

The two major features of this module are switching to the alernative screen and clearing the what is currenlty on the screen.

The [alternative screen](https://invisible-island.net/xterm/ctlseqs/ctlseqs.html#h2-The-Alternate-Screen-Buffer) is a feature of most terminals that allows an application to switch to a screen that has no scrollback, allowing it to draw whatever it wants to the terminal without interfering with the scrollback of the normal screen. This is most useful for full-screen applications, such as vim or emacs. Ansillary allows you to enter the alternative screen with the [`alternative`](@ref) function:

```julia-repl
julia> Screen.alternative() do
		   println("No scrollback!")
		   read(stdin, UInt8)
	   end
```

Ansillary will set raw mode (also known as [non-canonical mode](https://www.gnu.org/software/libc/manual/html_node/Canonical-or-Not.html)) when [`alternative`](@ref) is called as this is almost always what is wanted, to avoid this use the non-exported [`alternative!`](@ref) and [`standard!`](@ref) functions.

It also possible to only set raw mode using the [`raw`](@ref) function. The main benefits of raw mode are that the input stream is not line buffered allowing one byte to be read at a time (which in turn allows the application to respond to key presses), and that the input is not printed directly to the output allowing the application to handle printable input in it's own way (so that it can implement vim-style keybindings, for example).

To clear the screen Ansillary provides the [`clear!`](@ref) function, as well as the [`Area`](@ref) types for specifying which parts of the screen need clearing.

This short script

```julia
print("Some line...")
move!(Left(3))
clear!(FromCursorForward())
print("!")
```

will result in `Some line!` being printed to the terminal.

This module also provides the [`size`](@ref) as a slightly nicer wrapper around `displaysize`.
