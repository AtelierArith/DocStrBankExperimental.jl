```
approximate(f, domain)
```

連続または離散のドメイン上で適応的に有理補間を計算します。

# 引数

## 連続ドメイン

  * `f::Function`: 近似する関数
  * `domain`: ComplexRegionsからの曲線、パス、または領域

## 離散ドメイン

  * `f::Function`: 近似する関数
  * `z::AbstractVector`: 近似を行う点の集合

# キーワード

  * `max_iter::Integer=150`: ノード追加の最大反復回数
  * `float_type::Type`: 計算に使用する浮動小数点型¹
  * `tol::Real=1000*eps(float_type)`: 停止のための相対許容誤差
  * `allowed::Function`: 極が許可されているかを判断する関数²
  * `refinement::Integer=3`: 隣接ノード間のテストポイントの数（連続のみ）
  * `stagnation::Integer=20`: 停滞を判断するための反復回数

¹`float_type`のデフォルトは`float(1)`の昇格とドメインの浮動小数点型です。²デフォルトは、連続ドメインの曲線上または内部に極を許可しないこと、または離散ドメイン上のすべての極を受け入れることです。すべての極を許可するには`allowed=true`を使用します。

# 戻り値

  * `r::Approximation`: 有理補間

他にも[`Approximation`](@ref)、[`check`](@ref)、[`rewind`](@ref)を参照してください。

# 例

```julia-repl
julia> f = x -> tanh( 40*(x - 0.15) );

julia> r = approximate(f, unit_interval)
Barycentric{Float64, Float64} 有理関数の型 (22, 22) のドメイン: Path{Float64} で 1 つの曲線を持つ

julia> ( r(0.3), f(0.3) )
(0.9999877116508015, 0.9999877116507956)

julia> check(r);   # ドメイン全体の精度
[ Info: 最大誤差は 1.58e-13
```
