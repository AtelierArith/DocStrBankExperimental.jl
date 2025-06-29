```
HybridSystem{A, S, R, W, SV<:AbstractVector{S}, RV<:AbstractVector{R}, RW<:AbstractVector{W}} <: AbstractHybridSystem
```

ハイブリッドオートマトンとしてモデル化されたハイブリッドシステム。

### フィールド

  * `automaton`  – タイプ `A` のハイブリッドオートマトン。
  * `modes`      – 離散状態によってインデックス付けされたタイプ `S` のモードのベクター。                 ドメインとダイナミクスの両方がこのフィールドに格納されます。                 ドメインにアクセスするには [`stateset`](@ref) を参照してください。
  * `resetmaps`  – 遷移のラベルによってインデックス付けされたタイプ `R` のリセットマップのベクター。                 ガードはこのフィールドのマップの制約として格納されます。                 ガードにアクセスするには [`stateset`](@ref) を参照してください。
  * `switchings` – 遷移のラベルによってインデックス付けされたタイプ `W` のスイッチングのベクター。                 [`AbstractSwitching`](@ref) を参照してください。
  * `ext`        – 拡張によって使用できる辞書。

### 注意事項

タイプ `A` のオートマトン `automaton` は、異なる離散状態と対応するラベルを持つ許可された遷移をモデル化します。

モードのダイナミクスとドメインは、ベクター `modes` のタイプ `S` の連続ダイナミカルシステムに格納されています。これらはオートマトンの離散状態によってインデックス付けされています。

リセットマップとガードは、ベクター `resetmaps` のタイプ `R` のマップまたは離散ダイナミカルシステムとして与えられます。これらは対応する遷移のラベルによってインデックス付けされています。

タイプ `W` のスイッチングは、遷移のラベルによってインデックス付けされた `switchings` ベクターに与えられます。

追加のデータは `ext` フィールドに格納できます。

### 例

[サーモスタットの例](https://github.com/blegat/HybridSystems.jl/blob/master/examples/Thermostat.ipynb)を参照してください。
