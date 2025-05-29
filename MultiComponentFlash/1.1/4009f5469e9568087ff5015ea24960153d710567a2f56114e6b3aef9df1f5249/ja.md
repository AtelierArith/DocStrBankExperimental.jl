```
solve_rachford_rice(K, z, [V]; <keyword arguments>)
```

与えられた平衡定数 `K` とモル分率 `z` に対して、蒸気モル分率 `V` を計算します。

# 引数

`K` - `z` と同じ長さで、各成分の平衡定数を含みます。 `z` - モル分率。合計は1になる必要があります。

# キーワード引数

  * `tol = 1e-12`: 解法の許容誤差。
  * `maxiter=1000`: 最大反復回数
  * `ad=false`: 解析的勾配の代わりに自動微分（ForwardDiff）を使用します。
  * `analytical=true`: 2成分および3成分の解析解を使用します。

# 例

```julia-repl
julia> solve_rachford_rice([0.5, 1.5], [0.3, 0.7])
0.8000000000000002
```
