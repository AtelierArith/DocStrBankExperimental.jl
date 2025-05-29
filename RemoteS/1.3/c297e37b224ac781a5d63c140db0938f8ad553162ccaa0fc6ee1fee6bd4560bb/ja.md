```
VARI = vari(red, green, blue; kw...)
```

または（ここで fname は .png または .jpg ファイル名です）

```
VARI = vari(fname::String; kw...)
```

または

```
VARI = vari(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

可視大気抵抗指数。Gitelson, A.A., Kaufman, Y.J., Stark, R., Rundquist, D., 2002

VARI = (green - red) / (green + red - blue)

  * 最初の形式は、行列またはデータバンドのファイル名として入力を受け付けます。
  * 最後の形式はより多用途ですが、説明がより複雑です。

      * `cube`: 'cube' のファイル名で、通常は [`cutcube`](@ref) 関数で作成されるマルチレイヤーファイルです。このファイルがバンドの説明と共に作成された場合、`bands` または `bandnames` オプションを使用できます。
      * `bands`: [`cutcube`](@ref) で作成された *cubes* は、"Band1 ..." で始まる説明を他のバンドに割り当てます。したがって、`bands` が使用されると、"Band'band[k]'" という名前のバンドを検索します。ここで band[k] は `bands` ベクターのすべての要素をループします。警告: ベクター内の要素の順序は、波長番号が増加するようにソートされている必要があります。*すなわち*、最初の形式の例のように。
      * `layers`: キューブ内のバンドの順序が確実である場合、またはバンドの説明がない場合にこのオプションを使用します。選択は cube[:,:,layer[1]] などで行われます... 警告: 上記と同様の警告。
      * `bandnames`: バンドの一般的な名称、例えば "Green" やバンドの説明の一部、例えば "NIR" を知っている場合、その情報を使用して `bandnames` 文字列ベクターを作成し、キューブのバンドの説明と照合します。

### Kwargs

  * `threshold`: 閾値が提供されると、`vals[ij] < threshold = NaN` の GMTgrid を返します。
  * `classes`: 最大 3 要素（クラス区切り）のベクターで、`vals[ij] > classes[1] = 1; vals[ij] > classes[2] = 2; vals[ij] > classes[3] = 3` とそれ以外は 0 に分類された UInt8 GMTimage を返します。
  * `mask`: `threshold` と一緒に使用され、`vals[ij] >= threshold = 255` でそれ以外は 0 の UInt8 GMTimage マスクを出力します。`mask=-1`（または他の負の数）の場合、`vals[ij] < threshold = 255` でそれ以外は 0 のマスクを計算します。
  * `save`: `save="file_name.ext"` を使用して、結果をディスクファイルに保存します。ファイル形式はファイル拡張子から選択されます。
  * `order` | `bands_order` | `rgb`: $GLI$, $TGI$ および $VARI$ (RGB) 指数について、バンドの順序を再配置し、期待される RGB 順序を変更することを許可します。色の順序を含む文字列またはシンボルを渡します。例えば、`order=:rbg`

```
は緑と青の成分を入れ替え、結果のインデックスが _greens_ ではなく _reds_ を識別するようにします。
植生指数には適していませんが、他の目的には潜在的に有用です。
```

`bands`、`layers` または `bandnames` のいずれも提供されない場合、最初の形式に示されたデフォルトのバンド名を使用します。

インデックスとセンサーごとの適切なバンド名のリストについては、https://www.indexdatabase.de/ を参照してください。

`mask` または `classes` オプションが使用されている場合、Float32 GMTgrid または UInt8 GMTimage のいずれかを返します。
