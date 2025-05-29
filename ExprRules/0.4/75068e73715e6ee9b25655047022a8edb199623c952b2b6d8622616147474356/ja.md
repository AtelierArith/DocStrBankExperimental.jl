```
@grammar
```

文法を定義し、それをGrammarとして返します。例えば：

```julia-repl
grammar = @grammar begin
    R = x
    R = 1 | 2
    R = R + R
end
```
