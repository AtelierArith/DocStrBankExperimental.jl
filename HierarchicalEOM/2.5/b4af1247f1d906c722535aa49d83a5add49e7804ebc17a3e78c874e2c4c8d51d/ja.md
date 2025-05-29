```
struct ADOs
```

HEOMモデルの補助密度演算子。

# フィールド

  * `data` : ベクトル化された補助密度演算子
  * `dimensions` : 結合演算子の次元リスト（システムの次元と等しい必要があります）。
  * `N` : 補助密度演算子の数
  * `parity`: パリティラベル（`EVEN`または`ODD`）。

!!! note "`dims` プロパティ"
    与えられた `ados::ADOs` に対して、`ados.dims` または `getproperty(ados, :dims)` はその `dimensions` を整数ベクトルの型で返します。


# メソッド

特定のインデックス（`idx`）の密度行列を取得するには、次のように呼び出します： `ados[idx]`。 `HierarchicalEOM.jl` は次の呼び出し（メソッド）もサポートしています：

```julia
length(ados);  # `ADOs` の総数を返します
ados[1:idx];   # インデックス `1` から `idx` までの `ADO`（行列形式）を含むベクトルを返します
ados[1:end];   # すべての `ADO`（行列形式）を含むベクトルを返します
ados[:];       # すべての `ADO`（行列形式）を含むベクトルを返します
for rho in ados  # 繰り返し
    # 何かをする
end
```
