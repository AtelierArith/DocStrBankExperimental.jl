```
Replace(cols₁ => pred₁ => new₁, pred₂ => new₂, ..., colsₙ => predₙ => newₙ)
```

Replaces all values where `predᵢ` predicate returns `true` with `newᵢ` value  in the the columns selected by `colsᵢ`.

Passing a column selection is optional and when omitted all columns in the table  will be selected. The column selection can be a single column identifier (index or name),  a collection of identifiers, or a regular expression (regex).

The predicate can be a function that accepts a single argument and returns a boolean, or a value. If the predicate is a value, it will be transformed into the following function: `x -> x === value`.

# Examples

```julia
Replace(1 => -1, 5 => -5)
Replace(2 => 0.0 => 1.5, 5.0 => 5.5)
Replace(:b => 0.0 => 1.5, 5.0 => 5.5)
Replace("b" => 0.0 => 1.5, 5.0 => 5.5)
Replace([1, 3] => >(5) => 5)
Replace([:a, :c] => isequal(2) => -2)
Replace(["a", "c"] => (x -> 4 < x < 6) => 0)
Replace(r"[abc]" => (x -> isodd(x) && x > 10) => 2)
```

## Notes

  * Anonymous functions must be passed with parentheses as in the examples above.
  * Replacements are applied in the sequence in which they are defined, therefore, if there is more than one replacement for the same column, the first valid one will be applied.
