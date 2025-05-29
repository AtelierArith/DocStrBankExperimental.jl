```
entanglement(ρ::QuantumObject, sel; kwargs...)
```

[エンタングルメントエントロピー](https://en.wikipedia.org/wiki/Entropy_of_entanglement)を計算するために、`ρ`の部分トレースを行い、`sel`ベクターに含まれるインデックスを持つ次元のみを選択し、その後、フォン・ノイマンエントロピー[`entropy_vn`](@ref)を使用します。

# 注意事項

  * `ρ`は[`Ket`](@ref)または[`Operator`](@ref)のいずれかである必要があります。ただし、純粋状態である必要があります。
  * `sel`は残りのサブシステムのインデックスを指定します。詳細は[`ptrace`](@ref)を参照してください。
  * `kwargs`はフォン・ノイマンエントロピーを計算するためのキーワード引数です。詳細は[`entropy_vn`](@ref)を参照してください。
