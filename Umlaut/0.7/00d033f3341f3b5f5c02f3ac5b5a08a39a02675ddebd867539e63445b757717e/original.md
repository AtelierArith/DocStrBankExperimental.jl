```
bound(tape::Tape, v::Variable)
V(tape::Tape, v::Integer)
%(tape::Tape, i::Integer)
```

Create version of the var bound to an operation on the tape. The short syntax `tape %i` is convenient for working in REPL, but may surprise a reader of your code. Use it wisely.

# Examples:

```
V(3)                # unbound var
V(tape, 3)          # bound var
bound(tape, 3)      # bound var
bound(tape, V(3))   # bound var
tape %3             # bound var
```
