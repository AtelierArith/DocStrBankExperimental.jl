```
is_reduced(f::QuadBin{ZZRingElem}) -> Bool
```

Return whether `f` is reduced in the following sense. Let `f = [a, b, c]` be of discriminant `D`.

If `f` is positive definite (`D < 0` and `a > 0`), then `f` is reduced if and only if `|b| <= a <= c`, and `b >= 0` if `a = b` or `a = c`.

If `f` is negative definite (`D < 0` and `a < 0`), then `f` is reduced if and only if `[-a, b, -c]` is reduced.

If `f` is indefinite (`D > 0), then`f`is reduced if and only if`|sqrt{D} - 2|a|| < b < \sqrt{D}`or`a = 0`and`-b < 2c <= b`or`c = 0`and`-b < 2a <= b`.
