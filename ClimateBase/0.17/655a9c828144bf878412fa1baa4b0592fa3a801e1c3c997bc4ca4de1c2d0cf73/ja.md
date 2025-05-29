```
ncread(file, var [, selection]; kwargs...) → A
```

`file`から変数`var`を読み込み、適切な次元マッピングを持つ[`ClimArray`](@ref)に変換し、変数属性を辞書として含めます。次元属性は、存在する場合、`A`の次元にも与えられます。非構造化グリッドの仕様については、以下のキーワードを参照してください。

`file`は、`.nc`ファイルへの文字列であることができます。また、異なる`.nc`データ（通常は時間で分割されたもの）を遅延的に結合することを可能にする`NCDataset`であることもできます。例えば：

```julia
using Glob # すべてのファイルを取得するため
alldata = glob("toa_fluxes_*.nc")
file = NCDataset(alldata; aggdim = "time")
A = ClimArray(file, "tow_sw_all")
```

`var`は、読み込む変数を示す`String`です。グループを含む`.nc`データの場合、`var`は特定のグループから特定の変数を読み込むタプル`("group_name", "var_name")`であることもできます。この場合、グループとCF変数の両方の属性が作成された[`ClimArray`](@ref)に付与されます。

オプションで、フル配列の小さな部分を選択するための`selection`を提供できます。`selection`は、選択を構成するインデックスのタプルでなければならず、配列の次元と同じ数の範囲を正確に指定し、正しい順序で指定する必要があります。例えば、`var`が三次元の配列に対応する場合、次のような構文が可能です：

```julia
(:, :, 1:3)
(1:5:100, 1:1, [1,5,6])
```

関数[`ncsize`](@ref)は`selection`に役立つ場合があります。

また、[`ncdetails`](@ref)、[`nckeys`](@ref)、および[`ncwrite`](@ref)も参照してください。

## スマートローディング

`ncread`を使用してデータを読み込むことは、NCDatasets.jlを直接使用してから何らかの次元コンテナに変換しようとするよりもスマートです。

1. データは直接`ClimArray`に変換され、メタデータと次元名が保持されます。
2. データに欠損値がない場合（CF標準に従って）、返される配列は自動的に具体的な型に変換されます（すなわち、`Union{Float32, Missing}`は`Float32`になります）。
3. 範囲である次元（すなわち、一定のステップサイズでサンプリングされたもの）は、自動的に標準のJulia `Range`型に変換されます（これによりサブ選択が速くなります）。
4. 空間情報が直交グリッドにあるかどうかを自動的に推測し、そうでない場合は単一の`Coord`次元を作成します。

## キーワード

  * `name`は、読み込まれた配列の名前をオプションで変更します。
  * `grid = nothing`は、基盤となるグリッドが`grid = OrthogonalSpace()`または`grid = CoordinateSpace()`であるかどうかをオプションで指定します。詳細は[Types of spatial information](@ref)を参照してください。`nothing`の場合、次元の名前や`NCDataset`の他のキーに基づいて自動的に推測しようとします。
  * `lon, lat`。これらの2つのキーワードは、グリッド情報が*別の.ncファイル*で提供される非構造化グリッドデータで役立ちます。必要なのは、各グリッドポイントの中央経度と中央緯度のベクトルをユーザーが提供することです。これは、例えば次のように行います。

    ```julia
    ds = NCDataset("path/to/grid.nc");
    lon = Array(ds["clon"]);
    lat = Array(ds["clat"]);
    ```

    `lon, lat`が指定されている場合、`grid`は自動的に`CoordinateSpace()`と見なされます。
  * `celldim = nothing`：`CoordinateSpace`にのみ使用されます：次のとき`
