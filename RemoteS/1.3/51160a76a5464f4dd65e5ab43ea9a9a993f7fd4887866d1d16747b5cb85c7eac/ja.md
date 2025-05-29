```
GLI = gli(red, green, blue; kw...)
```

または（ここで fname は .png または .jpg ファイル名です）

```
GLI = gli(fname::String; kw...)
```

または

```
GLI = gli(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

グリーンリーフインデックス。Louhaichi, M., Borman, M.M., Johnson, D.E., 2001.

GLI = (2green - red - blue) / (2green + red + blue)

  * 最初の形式は、行列またはデータバンドのファイル名として入力を受け入れます。
  * 最後の形式はより多用途ですが、説明がより複雑です。

      * `cube`: 'cube' のファイル名で、通常は [`cutcube`](@ref) 関数で作成される多層ファイルです。このファイルがバンドの説明と共に作成された場合、`bands` または `bandnames` オプションを使用できます。
      * `bands`: [`cutcube`](@ref) で作成された *cubes* は、"Band1 ..." で始まる説明を他のバンドに割り当てます。したがって、`bands` が使用されると、"Band'band[k]'" という名前のバンドを検索します。ここで band[k] は `bands` ベクターのすべての要素をループします。警告: ベクター内の要素の順序は、波長番号が増加するようにソートされている必要があります。*すなわち*、最初の形式の例のように。
      * `layers`: キューブ内のバンドの順序が確実である場合、またはバンドの説明がない場合にこのオプションを使用します。選択は cube[:,:,layer[1]] などで行われます... 警告: 上記と同じ警告。
      * `bandnames`: バンドの一般的な名称、例えば "Green" やバンドの説明の一部、例えば "NIR" を知っている場合、その情報を使用して `bandnames` 文字列ベクターを作成し、キューブのバンドの説明と照合します。

### Kwargs

  * `threshold`: 閾値が提供されると、`vals[ij] < threshold = NaN` の GMTgrid を返します。
  * `classes`: 最大 3 要素（クラス区切り）のベクターで、`vals[ij] > classes[1] = 1; vals[ij] > classes[2] = 2; vals[ij] > classes[3] = 3` でインデックスを分類し、それ以外は 0 になります。
  * `mask`: `threshold` と一緒に使用すると、`vals[ij] >= threshold = 255` で UInt8 GMTimage マスクを出力し、それ以外は 0 になります。`mask=-1`（または他の負の数）の場合、代わりに `vals[ij] < threshold = 255` でマスクを計算し、それ以外は 0 になります。
  * `save`: `save="file_name.ext"` を使用して、結果をディスクファイルに保存します。ファイル形式はファイル拡張子から選択されます。
  * `order` | `bands_order` | `rgb`: $GLI$、$TGI$、および $VARI$（RGB）インデックスについて、バンドの順序を再配置し、期待される RGB 順序を変更することを許可します。色の順序を含む文字列またはシンボルを渡します。例えば、`order=:rbg`

```
は緑と青の成分を入れ替え、結果のインデックスが _greens_ ではなく _reds_ を特定するようにします。
植生インデックスには良くありませんが、他の目的には潜在的に有用です。
```

`bands`、`layers`、または `bandnames` のいずれも提供されない場合、最初の形式に示されたデフォルトのバンド名を使用します。

インデックスとセンサーごとの適切なバンド名のリストについては、https://www.indexdatabase.de/ を参照してください。

`mask` または `classes` オプションが使用されている場合、Float32 GMTgrid または UInt8 GMTimage のいずれかを返します。
