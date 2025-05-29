```
LFSR(taps::NTuple{N, Int} ; seed = trues(N), mapping = (true, false))
```

指定されたタップによって生成された値を返す無限の状態を持つイテレータを作成します。タップはフィボナッチ表記を仮定して降順で指定する必要があります。

シフトレジスタはデフォルトで全てのビットが1に初期化されますが、`seed`キーワード引数を使用して異なる初期状態を指定することができます。

デフォルトでは、イテレータは`Bool`型の値を生成します。`mapping`キーワードを使用して、タプル`(outputwhentrue, outputwhenfalse)`を指定することで、異なるイテレータ出力値を設定できます。

# 例

```jl
# 周期16の最大長LFSRを作成
julia> l = LFSR((4,3))
LFSR{2, Bool}((4, 3), Bool[1, 1, 1, 1], (true, false))

# シーケンスから最初の5つの値を取得
julia> first(l, 5)
5-element Vector{Bool}:
 0
 0
 0
 1
 0

# `true`と`false`の出力をそれぞれ`1.0`と`-1.0`に変更
julia> l = LFSR((4,3), mapping = (1.0, -1.0))
LFSR{2, Float64}((4, 3), Bool[1, 1, 1, 1], (1.0, -1.0))

julia> first(l, 5)
5-element Vector{Float64}:
 -1.0
 -1.0
 -1.0
  1.0
 -1.0

# `lfsrtaps`を使用して長さ`2^16-1`のシーケンスを定義
julia> l = LFSR(lfsrtaps[16])
LFSR{4, Bool}((16, 15, 13, 4), Bool[1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1], (true, false))
```

`lfsrtaps`も参照してください。
