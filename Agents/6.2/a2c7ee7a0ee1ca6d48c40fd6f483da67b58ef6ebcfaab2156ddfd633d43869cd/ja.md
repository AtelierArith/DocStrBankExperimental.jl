```
abmplot(model::ABM; kwargs...) → fig, ax, abmobs
abmplot!(ax::Axis/Axis3, model::ABM; kwargs...) → abmobs
```

エージェントベースのモデルをプロットするために、各エージェントをマーカーとしてプロットし、エージェントの位置フィールドをプロット上の位置として使用します。同じ関数は、返された `abmobs` を使用してモデルの進化のためのカスタム合成プロットやアニメーションを作成するためにも使用されます。`abmplot` は、エージェントベースのモデルの進化のためのインタラクティブなGUIを起動するためにも使用されます。以下の「インタラクティビティ」を参照してください。

また、[`abmvideo`](@ref) および [`abmexploration`](@ref) も参照してください。

## キーワード引数

### エージェント関連

  * `agent_color, agent_size, agent_marker` : これらの3つのキーワードは、各エージェントがプロットされる色、サイズ、およびマーカーを決定します。それぞれは定数または *関数* であり、単一のエージェントを入力として受け取り、対応する値を出力します。モデルが `GraphSpace` を使用している場合、`agent_color, agent_size, agent_marker` 関数は、各位置（すなわちグラフのノード）における *イテラブルなエージェント* を受け取ります。

    定数を使用する場合: `agent_color = "#338c54", agent_size = 15, agent_marker = :diamond`

    関数を使用する場合:

    ```julia
    agent_color(a) = a.status == :S ? "#2b2b33" : a.status == :I ? "#bf2642" : "#338c54"
    agent_size(a) = 10rand()
    agent_marker(a) = a.status == :S ? :circle : a.status == :I ? :diamond : :rect
    ```

    2Dモデルの場合、`agent_marker` は `Makie.Polygon` インスタンスであることができ、各エージェントを任意のポリゴンとしてプロットします。この場合、ポリゴンを作成する際の原点 (0, 0) はエージェントの位置であると仮定されます。この場合、キーワード `agent_size` は意味を持たず、各ポリゴンには独自のサイズがあります。このポリゴンを変形するには、`scale, rotate_polygon` 関数を使用します。

    現在、3Dモデルは異なるマーカーを持つことをサポートしていません。そのため、`agent_marker` は関数であってはなりません。`Mesh` または 3D プリミティブ（例えば `Sphere` や `Rect3D`）である必要があります。
  * `offset = nothing` : `nothing` でない場合、エージェントを入力として受け取り、エージェントの位置に加算されるオフセット位置のタプルを出力する関数でなければなりません（重なりがある場合にのみ重要です）。
  * `agentsplotkwargs = ()` : エージェントをプロットする関数（通常は `scatter!`）に伝播される追加のキーワード引数。

### プリプロット関連

  * `heatarray = nothing` : モデルのプロパティ（行列）を空間上にヒートマップとしてプロットするキーワードです。その値は、`run!` のような関数に与えられる標準データアクセサーであり、シンボル（モデルプロパティを直接取得）またはモデルの関数のいずれかです。空間が `AbstractGridSpace` の場合、行列は基盤となる空間と同じサイズでなければなりません。`ContinuousSpace` の場合は、任意のサイズが機能し、空間の範囲にわたってプロットされます。例えば、`heatarray = :temperature` は Daisyworld の例で使用されます。しかし、`f(model) = create_matrix_from_model...` を定義し、`heatarray = f` と設定することもできます。ヒートマップは、モデルの進化中に自動的に更新されます。
  * `heatkwargs = NamedTuple()` : `heatarray` が `nothing` でない場合に `Makie.heatmap` 関数に与えられるキーワード。
  * `add_colorbar = true` : `heatarray` が `nothing` でない場合、ヒートマップの右側にカラーバーを追加するかどうか。`heatarray` を使用する場合は、カラーバーを自然に配置できるように `abmplot` を使用することを強く推奨します。
  * `static_preplot!` : ヒートマップの後、エージェントの前に何かをプロットする関数 `f(ax, abmplot)`。
  * `spaceplotkwargs = NamedTuple()` : 空間をプロットする際に使用されるキーワード。直接渡されます。

      * モデル空間が `OpenStreetMapSpace` の場合は `OSMMakie.osmplot!` に。
      * モデル空間が `GraphSpace` の場合は [`GraphMakie.graphplot!`](https://graph.makie.org/stable/#GraphMakie.graphplot) に。
  * `adjust_aspect = true`: 軸のアスペクト比をモデルの空間のアスペクト比に調整します。
  * `enable_space_checks = true`: モデル空間に関連するチェックを無効にするには `false` に設定します。

スタンドアロン関数 `abmplot` は、`figure` および `axis` という2つのオプションの `NamedTuple` も受け取り、これを使用して自動的に作成された `Figure` および `Axis` オブジェクトを変更できます。

# インタラクティビティ

## 進化関連

  * `add_controls::Bool`: `true` の場合、`abmplot` は「インタラクティブアプリケーションGUI」モードに切り替わり、モデルが `Agents.step!` を使用してインタラクティブに進化します。`add_controls` はデフォルトで `false` ですが、`params`（以下参照）が空でない限り `true` になります。`add_controls` は、[`abmexploration`](@ref) では常に `true` です。アプリケーションには次のインタラクティブ要素があります。

    1. 「ステップ」: シミュレーションを `dt` 時間だけ進めます。
    2. 「実行」: モデルの連続進化を開始/停止します。
    3. 「モデルをリセット」: インタラクティブアプリケーションを開始した直後の初期状態にモデルをリセットします。
    4. 2つのスライダーがアニメーション速度を制御します: 「dt」はプロットが更新される前にモデルを進化させる時間を決定し、「sleep」は更新間の `sleep()` 時間です。
  * `enable_inspection = add_controls`: `true` の場合、マウスオーバーでエージェントの検査を有効にします。
  * `dt = 1:50`: 各フレーム更新でモデルを前進させる時間である「dt」スライダーの値で、`step!(model, dt)` を呼び出します。これは、離散時間モデルの場合は `1:50` に、連続時間モデルの場合は `0.1:0.1:10.0` にデフォルト設定されています。
  * `params = Dict()` : これは、インタラクティブアプリケーションから構成可能なモデルのパラメータを決定する辞書です。`params` の各エントリは、`Symbol` と `AbstractVector` のペアであり、与えられたシンボルに名付けられたパラメータの可能な値の範囲を提供します（オンラインの例を参照）。パラメータスライダーで値を変更することは、「更新」ボタンを押した後に実際のモデルに伝播されます。

## データ収集関連

  * `adata, mdata, when`: `Agents.run!` のキーワード引数と同じです。`adata, mdata` のいずれかまたは両方が与えられた場合、データが収集され、`abmobs` に保存されます。詳細は [`ABMObservable`](@ref) を参照してください。同じキーワードは [`abmexploration`](@ref) のデータプロットを提供します。これにより、「データをクリア」ボタンが追加され、以前に収集されたエージェントおよびモデルデータが基盤となる `DataFrames` `adf`/`mdf` を空にすることによって削除されます。モデルのリセットとデータのクリアは独立したプロセスです。

カスタムインタラクティブプロットについては、[`ABMObservable`](@ref) のドキュメント文字列を参照してください。 ```
