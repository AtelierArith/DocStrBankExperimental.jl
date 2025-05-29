```julia
struct Multiplier{S, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

`Multiplier`を入力バス`input`と符号`signs`で構築します。`signs`は`*`および/または`/`のタプルです。`Multiplier`の出力関数`g`は次の形をしています。

$$
    y = g(u, t) =  \prod_{j = 1}^n s_k u_k
$$

ここで、`n`は`input`の長さ、$s_k$は`signs`の`k`番目の要素、$u_k$は`input`の`k`番目の値、$y$は`output`の値です。`signs`のデフォルト値はすべて`*`です。

# フィールド

  * `ops::Any`: 演算子
  * `input::Any`: 入力ポート
  * `output::Any`: 出力ポート
  * `readout::Any`: 読み出し関数
  * `trigger::Any`
  * `handshake::Any`
  * `callbacks::Any`
  * `name::Any`
  * `id::Any`

# 例

```jldoctest
julia> mlt = Multiplier(ops=(*, *, /));

julia> mlt.readout([3, 4, 5], 0.) == 3 * 4 / 5
true
```
