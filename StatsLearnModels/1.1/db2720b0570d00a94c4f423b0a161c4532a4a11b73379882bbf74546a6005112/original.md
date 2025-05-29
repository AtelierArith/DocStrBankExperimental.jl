```
Learn(train, model, features => targets)
```

Fits the statistical learning `model` to `train` table, using the selectors of `features` and `targets`.

# Examples

```julia
Learn(train, model, [1, 2, 3] => "d")
Learn(train, model, [:a, :b, :c] => :d)
Learn(train, model, ["a", "b", "c"] => 4)
Learn(train, model, [1, 2, 3] => [:d, :e])
Learn(train, model, r"[abc]" => ["d", "e"])
```
