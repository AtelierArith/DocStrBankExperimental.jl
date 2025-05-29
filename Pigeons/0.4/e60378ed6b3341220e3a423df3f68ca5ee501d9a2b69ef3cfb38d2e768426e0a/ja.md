A [`Base.@kwdef`](https://github.com/JuliaLang/julia/blob/79ceb8dbeab1b5a47c6bd664214616c19607ffab/base/util.jl#L514) 構造体は、パラレルテンパリングアルゴリズムを作成するために使用されます。

フィールド（デフォルト値はソースファイルを参照）：

  * `target`:  目標分布。
  * `seed`:  マスタ乱数シード。
  * `n_rounds`:  実行するラウンドの数。
  * `n_chains`:  使用するチェーンの数（ただし、`n_chains_variational`も参照してください）。
  * `n_chains_variational`:  パラレルテンパリングの変分レグに使用するチェーンの数。デフォルト値はゼロです。変分引数が指定されていない場合、この引数は何もしません。それ以外の場合、ゼロの値は基本的な単一レグ変分パラレルテンパリングに対応し、チェーンの数は`n_chains`引数から取得されます。正の値は「安定化された」二レグ変分パラレルテンパリングを生成します。その場合、事前参照レグのチェーンの数は`n_chains`から取得され、変分レグのチェーンの数はこの引数から取得されます。詳細は https://arxiv.org/abs/2206.00080 を参照してください。
  * `reference`:  参照分布（例：事前分布）、または何も指定せず固定参照が必要な場合（すなわち、変分推論が無効または二レグ変分推論が使用されている場合）、[`default_reference()`](@ref) が呼び出され、ターゲットのタイプに基づいて参照が自動的に決定されます。
  * `variational`:  変分参照ファミリー、または変分推論を無効にするための何も指定しない。
  * `checkpoint`:  各ラウンドの終了時にチェックポイントをディスクに書き込むべきかどうか。
  * `record`: シミュレーションから何を保存するかを決定します。[`recorder_builder`](@ref) 型の要素を持つベクター。
  * `checked_round`: [`run_checks()`](@ref) が実行されるラウンドインデックス。これらのチェックをスキップするには0に設定します。
  * `multithreaded`: マルチスレッドエクスプローラーを許可するかどうか。オーバーヘッドが発生するため、デフォルトではFalseです。
  * `explorer`:  使用する[`explorer`](@ref)、または何も指定しない場合は、[`default_explorer()`](@ref) を使用してターゲットのタイプに基づいてエクスプローラーを自動的に決定します。
  * `extractor`:  [`extract_sample`](@ref) および [`sample_names`](@ref) に渡され、[`traces`](@ref) のサンプルをどのように抽出するかを決定します。

    値`nothing`はデフォルトの動作を示します。ログポテンシャルのみを抽出するには、[`LogPotentialExtractor`](@ref) を使用します。
  * `show_report`: サンプリングレポートを表示しますか？
  * `extended_traces`: [`traces`](@ref) および [`disk`](@ref) レコーダーがすべてのチェーンのサンプルを保存するか（extended = true）、ターゲットのみのサンプルを保存するか（extended = false）。
