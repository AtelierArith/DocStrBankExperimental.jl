```
T8codeMesh(meshfile::AbaqusFile{NDIMS};
           mapping=nothing, polydeg=1, RealT=Float64,
           initial_refinement_level=0, unsaved_changes=true,
           boundary_symbols = nothing)
```

`T8codeMesh`のメインメッシュコンストラクタで、Abaqusメッシュファイル（`.inp`）から非構造的で適合するメッシュをインポートします。

曲線の非構造的`T8codeMesh`を作成するために、2つの戦略が利用可能です：

  * `HOHQMesh Abaqus`: [`HOHQMesh.jl`](https://github.com/trixi-framework/HOHQMesh.jl)によって作成された高次の曲線境界情報が`meshfile`に利用可能です。境界のメッシュ多項式次数`polydeg`は`meshfile`から提供されます。マッピングされたツリー座標の計算は、[`UnstructuredMesh2D`](@ref)に似た線形ブレンディングを用いた超有限補間で行われます。境界名情報も`meshfile`から解析され、特定のツリー上の各命名された境界で異なる境界条件を設定できます。
  * `Standard Abaqus`: デフォルトでは、`mapping=nothing`および`polydeg=1`で、これは`meshfile`から解析された情報を基に直線的なメッシュを作成します。マッピング関数が指定されると、次数`polydeg`の多項式補間子を介してマッピングされたツリー座標を計算します。この関数によって作成されたメッシュは、`boundary_symbols`が指定されていない場合、1つの境界`:all`のみを持ちます。`boundary_symbols`が指定されている場合、メッシュファイルは境界ノードを定義するノードセットのために解析され、境界エッジ（2D）および面（3D）が割り当てられます。

`mapping`および`polydeg`キーワード引数は、`HOHQMesh Abaqus`オプションでのみ使用されることに注意してください。`Standard Abaqus`ルーチンは、メッシュ`polydeg`を`meshfile`から直接取得し、内部で超有限マッピングを構築します。

特定の戦略は、コンストラクタが`meshfile`が[HOHQMesh.jl](https://github.com/trixi-framework/HOHQMesh.jl)で作成されたかどうかを確認するヘッダーに基づいて選択されます。Abaqusファイルヘッダーが`meshfile`に存在しない場合、`T8codeMesh`は`Standard Abaqus`によって作成されます。

デフォルトのキーワード引数`initial_refinement_level=0`は、ツリーの数が元の`meshfile`の要素の数と同じである森林に対応します。`initial_refinement_level`を増加させることで、シミュレーションが始まる前に`meshfile`に与えられたベースメッシュを均一に細分化し、より多くのツリーを持つ森林を作成できます。たとえば、2次元のベースメッシュが25要素を含む場合、`initial_refinement_level=1`を設定すると、初期の森林は`2^2 * 25 = 100`のツリーを生成します。

# 引数

  * `meshfile::AbaqusFile{NDIMS}`: 次元NDIMSのAbaqusメッシュファイルオブジェクトで、ファイルへの`path`が与えられます。

# オプションのキーワード引数

  * `mapping`: インポートされたメッシュを物理ドメインに変換するマッピングを記述する`NDIMS`変数の関数。アイデンティティマップの場合は`nothing`を使用します。
  * `polydeg::Integer`: メッシュのジオメトリを格納するために使用される多項式次数。マッピングは、各ツリーの指定された次数の補間多項式によって近似されます。デフォルトの`1`は曲線のないジオメトリを作成します。インポートされた曲線のないメッシュを曲げる場合は、より高い値を使用してください。
  * `RealT::Type`: 座標に使用されるべき型。
  * `initial_refinement_level::Integer`: シミュレーションが始まる前にメッシュを均一にこのレベルまで細分化します。
  * `boundary_symbols::Vector{Symbol}`: `meshfile`内の境界名に対応するシンボルのベクター。`nothing`が渡されると、すべての境界は`:all`と名付けられます。
