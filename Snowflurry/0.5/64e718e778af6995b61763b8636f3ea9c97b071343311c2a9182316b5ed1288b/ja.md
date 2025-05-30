```
Readout <: AbstractInstruction
```

`Readout` は、特定のキュービットに対する明示的な測定を指定し、古典的な結果レジストリ（古典ビット）における宛先ビットを指定する `AbstractInstruction` の実装です。これは、最初の引数がターゲットキュービットで、2番目の引数が宛先の古典ビットである `readout(qubit::Int, bit::Int)` ヘルパー関数を使用して構築されます。測定は常に $Z$ 基底（計算基底とも呼ばれる）で行われます。

# 例

```jldoctest
julia> r = readout(1, 2)
Explicit Readout object:
   connected_qubit: 1 
   destination_bit: 2 

```
