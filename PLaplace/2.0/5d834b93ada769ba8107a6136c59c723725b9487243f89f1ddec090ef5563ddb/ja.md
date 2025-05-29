```
solve_plaplace(
    p::Float64,
    mesh::Mesh,
    g::Union{AbstractVector{Float64}, Function},
    dirichlet_boundary::Set{Boundary};
    <keyword arguments>
) -> PLaplaceData
```

与えられた問題に対する p-Laplace 演算子の解を返します。境界の（部分的な）ディリクレ条件が含まれます。さらに、体積ソース項と、交差しない境界の部分に対するノイマン条件を指定することもできます。解は、再定式化された問題に適用される内部点法によって計算されます。アルゴリズムの詳細については、ドキュメントの [algorithm](@ref algorithm-theory) ページを参照してください。

以下に、連続または離散的に指定できる関数と調整可能なパラメータを示す必須およびキーワード引数のリストがあります。さらに、出力は特にログおよび vtk ファイルが生成されるかどうかを制御できます。また、反復中にシステム行列の条件数を追跡することも可能ですが、これはパフォーマンスに大きな影響を与え、多くのメモリを必要とすることに注意してください。

# 必須引数

  * `p::Float64`: 問題のパラメータ。
  * `mesh::Mesh`: ドメインの FEM メッシュ。
  * `g::Union{AbstractVector{Float64}, Function}`: ディリクレ境界条件。
  * `dirichlet_boundary::Union{Set{Boundary}, Set{Int64}}`: ディリクレ条件を保持する物理境界の部分。名前付き境界のセットまたはノード ID で指定されます。

# キーワード引数

  * `f::Union{AbstractVector{Float64}, Function, Missing} = missing`:   離散または連続のソース項。
  * `neumann_boundary::Union{Set{Boundary}, Set{Int64}, Missing} = missing`:   ノイマン条件を保持する物理境界の部分。名前付き境界のセットまたは境界要素 ID で指定されます。
  * `h::Union{AbstractVector{Float64}, Function, Missing} = missing`:   離散または連続のノイマン境界条件。`neumann_boundary` を設定する必要があります。
  * `boundary_prolongation::Union{AbstractVector{Float64}, Missing} = missing`:   ディリクレ条件を全ドメインに延長するための指定された離散的延長。設定されていない場合、アルゴリズム中に計算されます。
  * `fixed_nodes::Union{Set{Boundary}, Set{Int64}, Missing} = missing,`:   固定ノードインデックスのセット、すなわち追加の均質なディリクレノード。名前付き境界のセットまたはノード ID で指定されます。`boundary_prolongation` が設定されている場合は無視されます。
  * `qdim::Int64 = 1`:   問題の成分数、すなわち f、g、h および u と v。ベクトル値設定の場合は必須です。
  * `eps::Float64 = 1e-6`:   解の精度。特に主経路追従の終了基準です。
  * `stepsize::Stepsize = ADAPTIVE`:   内部経路追従で代替のステッピングスキームを使用するための指定子。
  * `maxiterations::Int64 = 1000`:   内部経路追従スキームの各ステージごとの最大反復回数。
  * `kappa::Float64 = 10.0`:   長ステップ経路追従バリアントでのステップ長の更新に使用されるパラメータ。
  * `backtracking_maxiterations::Int64 = 25`:    長ステップ経路追従バリアントでの反復更新のためのバックトラッキング検索における最大反復回数。
  * `backtracking_decrementfactor::Float64 = 0.25`:   長ステップ経路追従バリアントのバックトラッキング検索における減少係数。
  * `solver::LinearSolver = CHOLESKY`:   線形システムに内部的に使用されるソルバーの指定子。
  * `preconditioner::Preconditioner = NONE`:   線形システムに内部的に使用される前処理器の指定子。
  * `useharmonicprolongation::Bool = true`:   境界条件を調和問題の解として延長するか、0 によって延長するかのフラグ。`boundary_prolongation` が設定されている場合は無視されます。
  * `vtkfile::Union{String,Missing} = missing`:   解を vtk に書き込むためのファイル名。設定されていない場合、ファイルは書き込まれません。
  * `verbose::Bool = true`:   反復中にログがコンソールに書き込まれるかどうかのフラグ。
  * `logfile::Union{String,Missing} = missing`:   ログをファイルに書き込むためのファイル名。設定されていない場合、ログはエクスポートされません。
  * `logcondition::Bool = false`:   システム行列の条件が追跡され、ログファイルに含まれるかどうかのフラグ。`logfile` が設定されている場合のみエクスポートされます。
