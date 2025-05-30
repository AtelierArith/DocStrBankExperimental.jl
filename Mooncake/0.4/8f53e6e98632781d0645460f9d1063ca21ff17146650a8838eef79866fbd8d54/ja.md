```
value_and_gradient!!(rule, f, x...)
```

`value_and_pullback!!(rule, 1.0, f, x...)` と同等で、`f` が `Union{Float16,Float32,Float64}` を返すことを前提としています。

*注意:* `value_and_pullback!!` を誤用する微妙な方法がたくさんあるため、可能な限り `Mooncake.value_and_gradient!!`（この関数）を使用することを一般的に推奨します。ただし、`value_and_pullback!!` のドキュメントはこの関数を理解するのに役立ちます。

例:

```jldoctest
f(x, y) = sum(x .* y)
x = [2.0, 2.0]
y = [1.0, 1.0]
rule = build_rrule(f, x, y)
value_and_gradient!!(rule, f, x, y)

# 出力

(4.0, (NoTangent(), [1.0, 1.0], [2.0, 2.0]))
```
