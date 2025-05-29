```
P4estMesh{NDIMS}(meshfile::String;
                 mapping=nothing, polydeg=1, RealT=Float64,
                 initial_refinement_level=0, unsaved_changes=true,
                 p4est_partition_allow_for_coarsening=true,
                 boundary_symbols = nothing)
```

`P4estMesh`のメインメッシュコンストラクタで、Abaqusメッシュファイル（`.inp`）から非構造的で適合するメッシュをインポートします。`meshfile`から解析された適合メッシュの各要素は、[`p4est`](https://github.com/cburstedde/p4est)ツリーデータ型として作成されます。

曲線/高次の非構造的メッシュ`P4estMesh`を作成するために、2つの戦略が利用可能です：

  * `p4est_mesh_from_hohqmesh_abaqus`: [`HOHQMesh.jl`](https://github.com/trixi-framework/HOHQMesh.jl)によって作成された高次（曲線）境界情報が`meshfile`に含まれています。境界のメッシュ多項式次数`polydeg`は`meshfile`から提供されます。マッピングされたツリー座標の計算は、[`UnstructuredMesh2D`](@ref)に似た線形ブレンディングを用いた超有限補間で行われます。境界名情報も`meshfile`から解析され、特定のツリーの各命名された境界で異なる境界条件を設定できるようになります。
  * `p4est_mesh_from_standard_abaqus`: デフォルトでは、`mapping=nothing`および`polydeg=1`で、`meshfile`から解析された情報を基に直線的なメッシュを作成します。マッピング関数が指定されると、次数`polydeg`の多項式補間を介してマッピングされたツリー座標を計算します。この関数によって作成されたメッシュは、`boundary_symbols`が指定されていない場合、1つの境界`:all`のみを持ちます。`boundary_symbols`が指定されている場合、`meshfile`は境界ノードを定義するノードセットのために解析され、境界エッジ（2D）および面（3D）が割り当てられます。

`mapping`および`polydeg`キーワード引数は、`p4est_mesh_from_standard_abaqus`関数でのみ使用されることに注意してください。`p4est_mesh_from_hohqmesh_abaqus`関数は、`meshfile`から直接メッシュ`polydeg`を取得し、内部で超有限マッピングを構築します。

特定の戦略は、コンストラクタが`meshfile`が[HOHQMesh.jl](https://github.com/trixi-framework/HOHQMesh.jl)で作成されたかどうかを確認するヘッダーに基づいて選択されます。Abaqusファイルヘッダーが`meshfile`に存在しない場合、`P4estMesh`は`p4est_mesh_from_standard_abaqus`関数で作成されます。

デフォルトのキーワード引数`initial_refinement_level=0`は、ツリーの数が元の`meshfile`の要素数と同じであるフォレストに対応します。`initial_refinement_level`を増加させることで、シミュレーションが始まる前に`meshfile`に与えられたベースメッシュを均一に細分化し、より多くのツリーを持つフォレストを作成できます。たとえば、2次元のベースメッシュに25の要素が含まれている場合、`initial_refinement_level=1`を設定すると、初期フォレストは`2^2 * 25 = 100`のツリーを作成します。

# 引数

  * `meshfile::String`: `p4est`によってインポート可能な非曲線Abaqusメッシュファイル。
  * `mapping`: インポートされたメッシュを物理ドメインに変換するマッピングを記述する`NDIMS`変数の関数。アイデンティティマップの場合は`nothing`を使用します。
  * `polydeg::Integer`: メッシュのジオメトリを格納するために使用される多項式次数。マッピングは、各ツリーの指定された次数の補間多項式によって近似されます。デフォルトの`1`は非曲線ジオメトリを作成します。インポートされた非曲線メッシュを曲げる場合は、より高い値を使用します。
  * `RealT::Type`: 座標に使用されるべき型。
  * `initial_refinement_level::Integer`: シミュレーションが開始される前に、このレベルまでメッシュを均一に細分化します。
  * `unsaved_changes::Bool`: `true`に設定すると、メッシュがメッシュファイルに保存されます。
  * `p4est_partition_allow_for_coarsening::Bool`: ドメインのパーティショニングに依存しないメッシュ適応性を持たせるために、AMRを使用する場合は`true`である必要があります。静的メッシュの場合は、より細かいパーティショニングを許可するために`false`にするべきです。
  * `boundary_symbols::Vector{Symbol}`: `meshfile`内の境界名に対応するシンボルのベクトル。`nothing`が渡されると、すべての境界が`:all`と名付けられます。
