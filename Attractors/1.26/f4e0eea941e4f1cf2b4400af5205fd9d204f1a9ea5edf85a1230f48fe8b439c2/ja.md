```
AttractorsViaRecurrences(ds::DynamicalSystem, grid; kwargs...)
```

初期条件 `ds` を状態空間の再帰に基づいてアトラクタにマッピングします。これは、[Datseris2022](@cite) に記載されているように、アトラクタをその場で特定することによって行われます。ただし、以下の説明セクションは、論文よりもアルゴリズムのより正確（かつ簡潔な）説明を提供しています。

`grid` は、有限サイズのセルに状態空間を分割するための指示です。これにより、有限状態機械がその上で動作できるようになります。可能性は次のとおりです。

1. 正規グリッド用のソートされた `AbstractRange` のタプル。

例として、`grid = (xg, yg)` で、`xg = yg = range(-5, 5; length = 100)` の二次元システムがあります。

2. 不規則グリッド用のソートされた `AbstractVector` のタプル。例えば、

`grid = (xg, yg)` で、`xg = range(0, 10.0^(1/2); length = 200).^2,   yg = range(-5, 5; length = 100)` です。

3. 特殊なグリッドタイプのインスタンス

[`SubdivisionBasedGrid`](@ref) で、手動で作成するか、[`subdivision_based_grid`](@ref) を使用して作成できます。これにより、異なる領域における状態空間の流れの速度に応じて、グリッドの離散化レベルが自動的に分析および適応されます。

グリッドは状態空間と同じ次元である必要があります。低次元の部分空間でアトラクタを検索したい場合は、[`ProjectedDynamicalSystem`](@ref) を使用してください。

## キーワード引数

  * `sparse = true`: 状態空間グリッドのストレージタイプを制御します。true の場合、スパース配列を使用します。これは、一般的に `sparse=false` で得られる通常の配列よりもメモリ使用量が効率的です。実際には、[`basins_fractions`](@ref) を検索する際には、スパース表現が常に推奨されます。非常に低次元のシステムや、完全な [`basins_of_attraction`](@ref) を計算する場合のみ、非スパースバージョンを使用する必要があります。

### 時間進化の設定

  * `Ttr = 0`: 再帰ルーチンが始まる前にトランジェントをスキップします。
  * `Δt`: 近似的な積分時間ステップ（`step!` 関数の第2引数）。`Δ`（`\Delta`）がアクセスできない場合は、キーワード `Dt` を代わりに使用できます。離散時間システムの場合は `1` です。連続システムの場合、自動的に値が計算され、[`automatic_Δt_basins`](@ref) を使用します。非常に細かいグリッドの場合、これは非常に小さくなり、適応型積分器の場合の典型的な内部ステップサイズよりもはるかに小さくなることがあります。そのような場合は、`stop_at_Δt = true` を使用してください。
  * `stop_at_Δt = false`: 入力ダイナミカルシステムが `CoupledODEs` の場合のみ使用されます。これは `step!` に第3の入力として与えられます。値 `true` は、(1) 非常に細かいグリッド、(2) 一部のアトラクタがリミットサイクルである場合に便利です。この場合、積分器のタイムステップがリミットサイクルの周期と同等になり、リミットサイクルを複数のアトラクタとして誤ってカウントすることになります。正確な [`convergence_time`](@ref) の推定が必要な場合は、`stop_at_Δt = true` も使用する必要があります。

### 有限状態機械の設定

  * `consecutive_recurrences = 100`: 新しいアトラクタに収束したと宣言する前に、以前に訪れたラベルのないセル（すなわち再帰）への連続訪問回数です。この数値はアトラクタへの収束の精度を調整し、一般的には高く（カオスシステムの場合はさらに高く）する必要があります。
  * `attractor_locate_steps = 1000`: 収束フェーズが終了した後、新しいアトラクタを正確に特定するために取られる後続のステップ数です。`attractor_locate_steps` ステップが取られた後、新しいアトラクタは十分な精度で特定され、反復が停止します。この数値は非常に高くても全体のパフォーマンスに大きな影響を与えません。
  * `store_once_per_cell = true`: 新しいアトラクタが見つかったときに、同じセルに属する状態空間の複数のポイントがアトラクタに保存されるかどうかを制御します。`true` の場合、訪れた各セルは1回だけポイントを保存します。これは固定点やリミットサイクルにとって望ましいです。`false` の場合、`attractor_locate_steps` ポイントがアトラクタごとに保存され、より密に保存されたアトラクタが生成されます。これは、例えばカオスアトラクタにとって望ましい場合があります。
  * `consecutive_attractor_steps = 2`: 既存のアトラクタセルへの連続ヒットの最大チェック数です。収束を宣言する前に。
  * `consecutive_basin_steps = 10`: 既存のアトラクタへの収束を宣言する前に必要な同じアトラクタの連続訪問回数です。`sparse = true` の場合は無視されます。なぜなら、その場合、盆地は内部に保存されないからです。
  * `consecutive_lost_steps = 20`: 定義されたグリッドの外での最大反復チェック数です。これを超えると、軌道が外部に失われたと宣言し、ラベル `-1` が割り当てられます。
  * `horizon_limit = 1e6`: 積分器の状態のノルムがこの制限に達した場合、軌道が無限大に発散したと宣言します。
  * `maximum_iterations = Int(1e6)`: 各初期条件に対して常に増加する安全カウンターです。これを超えると、アルゴリズムは `-1` を割り当て、警告を表示します。この条項は、不適切なグリッドに対してアルゴリズムが停止しないのを防ぐために存在します。新たに見つかったアトラクタの軌道が以前に見つかったアトラクタの同じセルに交差する場合（これによりすべてのカウンターが無限にリセットされる）に発生する可能性があります。

## 説明

`AttractorsViaRecurrences` のインスタンスに与えられた初期条件は、`ds` に対応する積分器に基づいて反復されます。状態空間における十分な再帰（すなわち、軌道が以前に訪れた領域を訪れたことを意味します）は、軌道がアトラクタに収束したことを示します。これがアトラクタを見つけるための基礎です。

有限状態機械（FSM）は、状態空間内の軌道を追跡し、与えられた `grid` のセルに常にマッピングします。グリッドセルは情報を保存します：それらは空、訪問済み、盆地、またはアトラクタセルです。FSMの状態は、セルのタイプとFSMの前の状態に基づいて決定されます。FSMがその状態を再帰するたびに、その内部カウンターが増加し、そうでない場合は0にリセットされます。内部カウンターがしきい値に達すると、FSMは終了するか、状態を変更します。終了の可能性は次のとおりです。

  * 軌道が `consecutive_recurrences` 回連続して以前に訪れたセルにヒットした場合：アトラクタが見つかったと見なされ、新しいIDでラベル付けされます。その後、`attractor_locate_steps` ステップの間、反復が続きます。この期間中に訪れた各セルは「アトラクタ」情報を保存します。その後、反復が終了し、初期条件はアトラクタのIDで番号付けされます。
  * 軌道が既に特定されたアトラクタに `consecutive_attractor_steps` 回連続してヒットした場合：初期条件はアトラクタの盆地IDで番号付けされます。
  * 軌道が既知の盆地に `consecutive_basin_steps` 回連続してヒットした場合：初期条件はその盆地に属し、適切に番号付けされます。盆地は `sparse = false` の場合にのみ保存され、使用されることに注意してください。それ以外の場合、この条項は無視されます。
  * 軌道が定義されたグリッドの外で `consecutive_lost_steps` ステップを過ごすか、ダイナミカルシステムの状態のノルムが `horizon_limit` を超えた場合：初期条件は `-1` とラベル付けされます。
  * 上記のいずれにも該当しない場合、初期条件は `maximum_iterations` ステップ後に `-1` とラベル付けされます。

ここでは説明しない特別な内部最適化や詳細がありますが、ソースコードのコメントに見つけることができます。（例えば、「失われた」状態のための特別なタイマーがあり、FSMのメインタイマーを中断しません。）

アルゴリズムの動作を示すビデオは、オンラインドキュメントの [recurrences animation](@ref recurrences_animation) ページで見つけることができます。 ```
