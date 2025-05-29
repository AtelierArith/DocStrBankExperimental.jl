```
Transformation(source_epsg, target_epsg; threaded=true, always_xy=false, proj_only=false)
```

2つの既知の座標参照系の間のパイプラインであるTransformationを作成します。Transformationは、[CoordinateTransformations.jl](https://github.com/JuliaGeometry/CoordinateTransformations.jl) APIを実装しています。

座標の変換を行うには、この構造体のインスタンスを関数のように呼び出します。以下に例を示します。これらの関数は、2つの数値または2つの数値ベクトルを受け入れます。

`source_crs`と`target_crs`は、EPSG権威コード（https://epsg.io/を参照）でなければなりません。例えば、「EPSG:3413」や3413::EPSGのようにです。作成されたパイプラインは、座標が公式定義の軸順序と軸単位を尊重することを期待します（例えば、EPSG:4326の場合、緯度が最初で経度が次に来る、度単位で）。同様に、ターゲットCRSのためにその構文を使用する場合、出力値はこのCRSの公式定義に従って発信されます。この動作は、`always_xy=true`を渡すことで上書きできます。

`threaded`はマルチスレッドをオンまたはオフにします。

`always_xy`は、オプションで軸の順序をx,yまたはlon,latの順序に固定できます。デフォルトでは`false`であり、これは与えられた座標参照系を担当する権威によって順序が定義されることを意味します。これは、[このPROJ FAQのエントリ](https://proj.org/faq.html#why-is-the-axis-ordering-in-proj-not-consistent)で説明されています。

`proj_only`は、FastGeoProjectionが利用可能な場合でも、TransformationsにPro.jlのみを使用するオプションです。デフォルトでは、FastGeoProjectionが利用できない場合にのみProj.jlが使用されます。

# 例

```julia
julia> trans = Proj.Transformation("EPSG:4326", "EPSG:28992", always_xy=true)
Transformation
    source: WGS 84 (with axis order normalized for visualization)
    target: Amersfoort / RD New

julia> trans(5.39, 52.16)  # これはlon,latの順序で、always_xyをtrueに設定したためです
(155191.3538124342, 463537.1362732911)
```
