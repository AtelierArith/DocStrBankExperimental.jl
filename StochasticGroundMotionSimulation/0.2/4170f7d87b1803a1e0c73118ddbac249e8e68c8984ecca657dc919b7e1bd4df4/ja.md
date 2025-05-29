```
magnitude_to_moment(m::T) where T<:Real
```

モーメントマグニチュードを地震モーメント（ダイン-センチメートル単位）に変換します。

# 例

```julia-repl
	m = 6.0
	M0 = magnitude_to_moment(m)
```
