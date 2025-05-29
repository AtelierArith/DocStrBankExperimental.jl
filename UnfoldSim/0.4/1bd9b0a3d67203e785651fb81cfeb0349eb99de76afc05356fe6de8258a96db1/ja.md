```
simulate(
rng::AbstractRNG,
design::AbstractDesign,
components,
onset::AbstractOnset,
noise::AbstractNoise = NoNoise();
return_epoched = false,
)

simulate(
design::AbstractDesign,
components,
onset::AbstractOnset,
noise::AbstractNoise = NoNoise();
return_epoched = false,
)
```

`design`、`component`の[配列]、`onset`、オプションの`noise`および`rng`を指定して、連続またはエポック信号をシミュレートします。主なシミュレーション関数です。

# 引数

  * `rng::AbstractRNG`（オプション）：再現性を確保するために重要な乱数生成器。
  * `design::AbstractDesign`：希望する実験デザイン。
  * `components`：希望する信号の`Component`。
  * `onset::AbstractOnset`：希望する発生間隔分布。
  * `noise::AbstractNoise = NoNoise()`（オプション）：希望するノイズ。

# キーワード引数

  * `return_epoched::Bool = false`：`true`に設定するとエポックデータが返され、それ以外の場合は連続信号が返されます（以下のノートも参照）。

# 戻り値

  * `(signal, events)::Tuple{Array, DataFrame}`：

      * `signal` : 生成された信号。デザイン、コンポーネント、`return_epoched`に応じて、出力は1-D、2-D、3-Dまたは4-Dの配列になる可能性があります。例えば、4-D配列は`channels x time x trials x subjects`の次元を持ちます。
      * `events`：遅延を持つ生成されたイベントデータフレーム。

# 例

UnfoldSimドキュメントの[クイックスタートチュートリアル](https://unfoldtoolbox.github.io/UnfoldSim.jl/stable/generated/tutorials/quickstart/)からの適応。

```julia-repl
julia> using Random # RNGを取得するために

julia> design =
    SingleSubjectDesign(; conditions = Dict(:cond_A => ["level_A", "level_B"])) |>
    x -> RepeatDesign(x, 10);

julia> component = LinearModelComponent(; 
    basis = [0, 0, 0, 0.5, 1, 1, 0.5, 0, 0],
    formula = @formula(0 ~ 1 + cond_A),
    β = [1, 0.5],
);

julia> onset = UniformOnset(; width = 20, offset = 4);

julia> noise = PinkNoise(; noiselevel = 0.2);

# バリアント 1: カスタムRNGを使用。
julia> data, events = simulate(MersenneTwister(2), design, component, onset, noise);

julia> data
293-element Vector{Float64}:
 -0.013583193323430123
  0.09159433856866195
  ⋮
 -0.25190584567097907
 -0.20179992275876316

julia> events
20×2 DataFrame
 Row │ cond_A   latency 
     │ String   Int64   
─────┼──────────────────
   1 │ level_A        9
   2 │ level_B       20
   3 │ level_A       27
   4 │ level_B       37
  ⋮  │    ⋮        ⋮
  18 │ level_B      257
  19 │ level_A      271
  20 │ level_B      284
         13 rows omitted

# バリアント 2: RNGを指定せずに、MersenneTwister(1)がシミュレーションに使用されます。
julia> data1, events1 = simulate(design, component, onset, noise);
┌ Warning: 乱数生成器が定義されていません、デフォルト（`Random.MersenneTwister(1)`）が固定シードで使用されました。これにより常に同じ結果が返され、ユーザーは自分の乱数生成器を提供することを強く推奨されます！
```

# ノート

ノイズの追加方法に関するいくつかの注意事項：

  * `return_epoched = true`で`onset = NoOnset()`の場合、ノイズはエポックデータ行列に追加されます。
  * `onset`が`NoOnset`でない場合、連続信号が作成され、ノイズがこれに追加されます。つまり、`return_epoched = true`の場合でも、`onset = NoOnset()`のケースとはノイズが同じではありません。
  * `return_epoched = false`および`onset = NoOnset()`のケースは不可能であり、したがってアサート文でカバーされています。

`return_epoched = true`のときの隣接信号の重なりに関する追加の注意事項：

  * `onset = NoOnset()`の場合、データに重なり合う信号はありません。なぜなら、発生計算と連続信号への変換がスキップされるからです。
  * 発生間隔分布が与えられた場合、重なりのある可能性のある連続信号が構築され、その後エポックに分割されます。
