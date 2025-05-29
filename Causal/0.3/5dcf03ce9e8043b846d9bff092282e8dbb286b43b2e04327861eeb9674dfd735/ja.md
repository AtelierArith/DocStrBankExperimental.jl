```julia
struct Gain{G, IP, OP, RO, var"356", var"357", var"358", Symbol, var"359"} <: Causal.AbstractStaticSystem
```

`Gain`を構築し、その出力関数`g`は次の形をしています 

$$
    y = g(u, t) =  K u
$$

ここで、$K$は`gain`、$u$は`input`の値、$y$は`output`の値です。

# フィールド

  * `gain::Any`: ゲイン
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
julia> K = [1. 2.; 3. 4.];

julia> sfunc = Gain(input=Inport(2), gain=K);

julia> sfunc.readout([1., 2.], 0.) == K * [1., 2.]
true
```
