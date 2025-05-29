A switch statement of sorts:

```
@switch x begin
  1; "x equals one!"
  2; "x equals two!"
  "x equals something else!"
end
```

However, it's a bit more general than a regular switch in that you can test more than just equality:

```
@switch isa(x, _) begin
  Integer; "x is an integer!"
  FloatingPoint; "x is a float!"
  "x is something else!"
end

@switch _ begin
  a > b;  "more than!"
  a < b;  "less than!"
  a == b; "equal!"       # Note that this level of enthusiasm is not mandatory.
end
```

Where `_` is replaced by the value for testing in each case. The final expression, if there is one, is used as the default value; if there is no default and nothing matches an error will be thrown.
