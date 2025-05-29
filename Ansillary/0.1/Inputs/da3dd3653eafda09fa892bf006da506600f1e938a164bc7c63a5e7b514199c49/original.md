This module deals with reading events from the terminal.

Mostly these events will be input from the user, but some of the functionality is about the *terminal* sending messages as well.

The fundamental piece of functionality that this module offers is being able to a single event from an input stream.

```jldoctest
julia> read(IOBuffer("[7;2~"), Event)
Shift+Home
```

If Ansillary does not recognise an event it will return the bytes that it has read *and any remaining bytes in the stream*.

```jldoctest
julia> read(IOBuffer("[Q[7;2~"), Event)
Ansillary.Inputs.Unknown(UInt8[0x1b, 0x5b, 0x51, 0x1b, 0x5b, 0x37, 0x3b, 0x32, 0x7e])
```

This is done to minimise the risk of the application receiving a seemingly valid event that is actually part of an unknown event, which could lead to highly undesirable consequences. Note that **this is not completely foolproof**, for example Konsole sends `"@sy"` when Super+y is pressed and Ansillary will happily accept that as four separate events.

```jldoctest
julia> let input = IOBuffer("@sy"); [read(input, Event), read(input, Event), read(input, Event), read(input, Event)] end
4-element Array{Ansillary.Inputs.Key,1}:
 Ctrl+x
 @
 s
 y
```

[`Events`](@ref) is an iterator that wraps `read(::Any, ::Event)`, see the file `examples/keylogger.jl` to see how that works. [`EventLoop`](@ref) is an iterator that also sends a [`Tick`](@ref) event every `period`, see the file `examples/snake.jl` or `tests/interactive.jl` to see how that works (also make sure to pay attention to the warnings on that type's documentation).

This module also contains the [`paste`](@ref) function, which allows you to turn on bracketed paste mode. In bracketed paste mode when the user pastes something into the terminal, a [`PasteStart`](@ref) event will be sent, followed by the pasted text, then finally a [`PasteEnd`](@ref) event.

!!! warning
    The functionality of this module will only work properly if the terminal is in raw mode, e.g.

    ```julia
    Screen.raw() do
    	for key in Events(stdin)
    		@show key
    		if key == CTRL_C
    			break
    		end
    	end
    end
    ```

