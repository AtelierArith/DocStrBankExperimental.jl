```
dive(s)
```

Inspect an instance of system `s` by navigating hierarchy of variables displayed in a tree structure.

Pressing up/down arrow keys allows navigation. Press 'enter' to dive into a deeper level and press 'q' to come back. A leaf node of the tree shows an output of `look` regarding the variable. Pressing 'enter' again would return a variable itself and exit to REPL.

Only works in a terminal environment; not working on Jupyter Notebook.

See also: [`look`](@ref)

# Arguments

  * `s::System`: instance of target system.

# Examples

```julia-repl
julia> @system S(Controller) begin
           a => 1 ~ preserve(parameter)
       end;

julia> s = instance(S);

julia> dive(s)
S
 → context = <Context>
   config = <Config>
   a = 1.0
```
