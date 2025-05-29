```
NDWI = ndwi(green, nir; kw...)
```

または

```
NDWI = ndwi(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

正規化差水指数。McFeeters 1996。NDWI => (green - nir)/(green + nir)

NDWI = (green - nir)/(green + nir)

  * 最初の形式は、行列またはデータバンドのファイル名を入力として受け入れます。
  * 最後の形式はより多用途ですが、説明がより複雑です。

      * `cube`: 'cube'のファイル名で、通常は[`cutcube`](@ref)関数で作成される多層ファイルです。このファイルがバンドの説明と共に作成された場合、`bands`または`bandnames`オプションを使用できます。
      * `bands`: [`cutcube`](@ref)で作成された*cubes*は、"Band1 ..."で始まる説明を他のバンドに割り当てます。したがって、`bands`が使用されると、"Band'band[k]'"という名前のバンドを検索します。ここで、band[k]は`bands`ベクターのすべての要素をループします。警告: ベクター内の要素の順序は、波長番号が増加するようにソートされている必要があります。*すなわち*、最初の形式の例のように。
      * `layers`: キューブ内のバンドの順序が確実である場合、またはバンドの説明がない場合にこのオプションを使用します。選択はcube[:,:,layer[1]]などで行われます... 警告: 上記と同じ警告。
      * `bandnames`: バンドの一般的な名称、例えば"Green"やバンドの説明の一部、例えば"NIR"がわかっている場合、その情報を使用して`bandnames`文字列ベクターを作成し、キューブのバンドの説明と照合します。

### Kwargs

  * `threshold`: 閾値が提供されると、`vals[ij] < threshold = NaN`のGMTgridを返します。
  * `classes`: 最大3つの要素（クラス区切り）を持つベクターで、`vals[ij] > classes[1] = 1; vals[ij] > classes[2] = 2; vals[ij] > classes[3] = 3`およびそれ以外は0に分類されたUInt8 GMTimageを返します。
  * `mask`: `threshold`と一緒に使用され、`vals[ij] >= threshold = 255`およびそれ以外は0のUInt8 GMTimageマスクを出力します。`mask=-1`（または他の負の数）の場合、代わりに`vals[ij] < threshold = 255`およびそれ以外は0のマスクを計算します。
  * `save`: `save="file_name.ext"`を使用して、結果をディスクファイルに保存します。ファイル形式はファイル拡張子から選択されます。
  * `order` | `bands_order` | `rgb`: $GLI$、$TGI$、および$VARI$（RGB）インデックスの場合、バンドの順序を再配置し、期待されるRGB順序を変更することを許可します。色の順序を持つ文字列またはシンボルを渡します。例えば、`order=:rbg`

```
は緑と青の成分を入れ替え、結果のインデックスが_緑_の代わりに_赤_を特定するようにします。
植生指数には適していませんが、他の目的には潜在的に有用です。
```

`bands`、`layers`、または`bandnames`のいずれも提供されない場合、最初の形式に示されているデフォルトのバンド名を使用します。

インデックスとセンサーごとの適切なバンド名のリストについては、https://www.indexdatabase.de/を参照してください。

`mask`または`classes`オプションが使用されている場合、Float32 GMTgridまたはUInt8 GMTimageのいずれかを返します。
