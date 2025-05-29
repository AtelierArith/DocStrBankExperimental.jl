```
CartData(x::Any, y::Any, z::GeoUnit, fields::NamedTuple)
```

データ構造は、直交座標系の x/y/z 座標を持つ1つまたは複数のフィールドを保持します。距離はキロメートル単位です。

  * `x`,`y`,`z` はメートル、キロメートルの単位を持つか、単位なしであることができ、キロメートルに変換されます。
  * `fields` は理想的には各フィールドの名前を指定できる NamedTuple であるべきです。
  * 1つの配列のみを渡した場合、デフォルト名の NamedTuple に変換されます。
  * 単一のフィールドは `(DataFieldName=Data,)` のように追加する必要があります（最後のカンマを忘れないでください）。
  * 複数のフィールドも追加できます。
  * ベクトルフィールドを paraview で表示したい場合は、タプルとして追加します: `(Velocity=(Vx,Vnorth,Vup), Veast=Veast, Vnorth=Vnorth, Vup=Vup)`; これを `ParaviewData` 構造に変換する際に自動的にベクトル変換が適用され、Paraview 出力が生成されます。これにより矢印の大きさが変わるため、Paraview では `[Veast,Vnorth,Vup]` コンポーネントは表示されなくなります。したがって、これらを別々のフィールドとして保存するのは良いアイデアです。
  * ただし、1つの例外があります: 3成分フィールドの名前が `colors` の場合、このフィールドは RGB 色を含むと見なされるため、ベクトル変換は適用されません。
  * `x`,`y`,`z` は `Data` 配列と同じサイズである必要があります。配列の順序は重要です。3D 配列の場合、以下の例のように、最初の次元が `x`、2番目の次元が `y`、3番目の次元が `z`（キロメートル単位）に対応すると仮定します。以下に例を示します。

# 例

```julia-repl
julia> x        =   0:2:10
julia> y        =   -5:5
julia> z        =   -10:2:2
julia> X,Y,Z    =   xyz_grid(x, y, z);
julia> Data     =   Z
julia> Data_set =   CartData(X,Y,Z, (FakeData=Data,Data2=Data.+1.))
CartData
    size    : (6, 11, 7)
    x       ϵ [ 0.0 km : 10.0 km]
    y       ϵ [ -5.0 km : 5.0 km]
    z       ϵ [ -10.0 km : 2.0 km]
    fields  : (:FakeData, :Data2)
  attributes: ["note"]
```

`CartData` は、直交グリッドを必要とする LaMEM などの直交地球物理コードと組み合わせて特に便利です。データを Paraview に直接保存できます。

```julia-repl
julia> write_paraview(Data_set, "Data_set")
1-element Vector{String}:
 "Data_set.vts"
```

必要に応じて、これを `UTMData` に変換できます（単に変換します）。

```julia-repl
julia> Data_set1 =  convert(GeoData, Data_set)
GeoData
  size  : (116, 96, 25)
  lon   ϵ [ 14.075969111533457 : 14.213417764154963]
  lat   ϵ [ 40.77452227533946 : 40.86110443583479]
  depth ϵ [ -5.4 km : 0.6 km]
  fields: (:FakeData, :Data2)
```

これにより、通常の方法で paraview で視覚化することができます。
