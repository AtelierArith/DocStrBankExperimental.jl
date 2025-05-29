```
get_array(
    fr::FieldRecord [, allselectargs::NamedTuple];
    coords=nothing,
    lookup_coords=true,
    add_attributes=true,
    update_name=true,
    omit_recorddim_if_constant=false, 
) -> fa_out::FieldArray

[deprecated] get_array(fr::FieldRecord [; kwargs...] [; allselectargs...]) -> fa_out::FieldArray
```

[`FieldArray`](@ref) を返し、`allselectargs` で定義されたレコードと空間領域の値の配列と、添付された座標を含みます。

[`FieldArray(fr::FieldRecord)`](@ref) と [`select(fa::FieldArray)`](@ref) を組み合わせます。

オプションの `allselectargs` フィールド `expand_cartesian` (デフォルトは `false`) は、`CartesianLinearGrid` を使用した空間的に解決された出力にのみ必要で、圧縮された内部データ (空間次元 `cells` を持つ) を直交配列 (空間次元は例えば `lon`, `lat`, `zt`) に展開するために `true` に設定します。

# キーワード引数

[`FieldArray(fr::FieldRecord)`](@ref) と [`select(fa::FieldArray)`](@ref) を参照してください。

# 例

  * 単一セルインデックス 3 の時系列を選択する：

    ```
    get_array(fr, (cell=3, ))
    ```
  * モデル時間 10.0 に最も近い時間で最初の列を選択する：

    ```
    get_array(fr, (column=1, tmodel=10.0))
    ```
  * モデル時間 10.0 に最も近い時間で最初の列を設定し、大気モデルの圧力座標を z 座標で置き換える：

    ```
    get_array(
        fr, (column=1, tmodel=10.0);
        coords=["cells"=>("atm.zmid", "atm.zlower", "atm.zupper")]
    )
    ```
  * モデル時間 10.0 に最も近い時間で 3D 出力から 2D 配列 (次元 `zt`, インデックス 1) を選択し、`CartesianLinearGrid` を展開する：

    ```
    get_array(fr, (zt_isel=1, tmodel=10.0, expand_cartesian=true))
    ```
  * モデル時間 10.0 に最も近い時間で 3D 出力から 200 度の経度に最も近いインデックスで 2D 配列を選択し、`CartesianLinearGrid` を展開する：

    ```
    get_array(fr, (lon=200.0, tmodel=10.0, expand_cartesian=true))
    ```
  * netcdf 出力に使用されるフルデータキューブを取得し、座標と属性を省略し、シングルトン次元を保持し、変数が定数の場合はレコード次元を省略する：

    ```
    get_array(
        fr, (expand_cartesian=true, squeeze_all_single_dims=false);
        lookup_coordinates=false, add_attributes=false, omit_recorddim_if_constant=true
    )
    ```

# 制限事項

  * 各次元について、単一のスライスまたは連続した範囲を選択することは可能ですが、インデックスまたは座標値のベクトルに対してスライスのセットを選択することはできません。
