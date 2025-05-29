```
compile(re::RE; optimize::Bool=true, unambiguous::Bool=true)::Machine
```

Compile a finite state machine (FSM) from `re`. If `optimize`, attempt to minimize the number of states in the FSM. If `unambiguous`, disallow creation of FSM where the actions are not deterministic.

# Examples

```
machine = let
    name = re"[A-Z][a-z]+"
    first_last = name * re" " * name
    last_first = name * re", " * name
    compile(first_last | last_first)
end
```
