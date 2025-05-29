```
run!(object, meteo, constants, extra=nothing; check=true, executor=Floops.ThreadedEx())
run!(object, mapping, meteo, constants, extra; nsteps, outputs, check, executor)
```

モデルリスト内の各モデルについて、依存関係グラフを尊重して正しい順序でシミュレーションを実行します。

複数の時間ステップが与えられた場合、モデルは各時間ステップについて逐次的に実行されます。

# 引数

  * `object`: [`ModelList`](@ref)、`ModelList`の配列または辞書、または植物グラフ（MTG）。
  * `meteo`: [`PlantMeteo.TimeStepTable`](https://palmstudio.github.io/PlantMeteo.jl/stable/API/#PlantMeteo.TimeStepTable) の

[`PlantMeteo.Atmosphere`](https://palmstudio.github.io/PlantMeteo.jl/stable/API/#PlantMeteo.Atmosphere) または単一の `PlantMeteo.Atmosphere`。

  * `constants`: [`PlantMeteo.Constants`](https://palmstudio.github.io/PlantMeteo.jl/stable/API/#PlantMeteo.Constants) オブジェクト、または定数キーと値の `NamedTuple`。
  * `extra`: 植物グラフのシミュレーションには利用できない追加パラメータ（シミュレーションオブジェクトはこれを使用して渡されます）。
  * `check`: `true` の場合、シミュレーションを実行する前にモデルリストの有効性をチェックします（少し時間がかかります）、実行中により多くの情報を返します。
  * `executor`: シミュレーションを逐次的に（`executor=SequentialEx()`）、マルチスレッド方式で（`executor=ThreadedEx()`、デフォルト）、または分散方式で（`executor=DistributedEx()`）実行するために使用される [`Floops`](https://juliafolds.github.io/FLoops.jl/stable/) エグゼキュータ。
  * `mapping`: MTGとモデルリストの間のマッピング。
  * `nsteps`: 実行する時間ステップの数、メテオが与えられていない場合のみ必要（そうでなければそれから推測されます）。
  * `outputs`: MTGの各ノードタイプに対して動的に取得する出力。

# 戻り値

オブジェクトの状態をインプレースで変更します。ユーザーは [`status`](https://virtualplantlab.github.io/PlantSimEngine.jl/stable/API/#PlantSimEngine.status-Tuple{Any}) 関数を使用してオブジェクトから結果を取得できます（例を参照）。

# 詳細

## モデル実行

モデルは依存関係グラフに従って実行されます。モデルが別のモデルに対してソフト依存関係を持つ場合（すなわち、その入力が別のモデルによって計算される場合）、他のモデルが最初に実行されます。モデルが複数のソフト依存関係を持つ場合、親（ソフト依存関係）は常に最初に計算されます。

## 並列実行

ユーザーは、`executor` 引数に互換性のあるエグゼキュータを提供することで並列実行を要求できます。このパッケージは、実行が並列化できるかどうかも自動的にチェックします。そうでない場合、ユーザーが並列計算を要求した場合は警告を返し、シミュレーションを逐次的に実行します。シミュレーションを並列で実行するために [`Floops`](https://juliafolds.github.io/FLoops.jl/stable/) パッケージを使用します。つまり、`executor` 引数に互換性のあるエグゼキュータを提供できます。追加のスレッドベースのエグゼキュータについては [FoldsThreads.jl](https://github.com/JuliaFolds/FoldsThreads.jl) を、Dagger.jlフレームワークを使用して実装されたTransducers.jl互換の並列フォールドについては [FoldsDagger.jl](https://github.com/JuliaFolds/FoldsDagger.jl) を、そして近日中にGPU計算のための [FoldsCUDA.jl](https://github.com/JuliaFolds/FoldsCUDA.jl) をご覧ください（[この問題](https://github.com/VirtualPlantLab/PlantSimEngine.jl/issues/22)を参照）および [FoldsKernelAbstractions.jl](https://github.com/JuliaFolds/FoldsKernelAbstractions.jl)。自動並列化が可能かどうかを確認するには [ParallelMagics.jl](https://github.com/JuliaFolds/ParallelMagics.jl) をご覧ください。

# 例

パッケージをインポートします: 

```jldoctest run
julia> using PlantSimEngine, PlantMeteo;
```

`Examples` サブモジュールに示されたダミーモデルをロードします:

```jldoctest run
julia> using PlantSimEngine.Examples;
```

モデルリストを作成します:

```jldoctest run
julia> models = ModelList(Process1Model(1.0), Process2Model(), Process3Model(), status = (var1=1.0, var2=2.0));
```

メテオデータを作成します:

```jldoctest run
julia> meteo = Atmosphere(T=20.0, Wind=1.0, P=101.3, Rh=0.65, Ri_PAR_f=300.0);
```

シミュレーションを実行します:

```jldoctest run
julia> outputs_sim = run!(models, meteo);
```

結果を取得します:

```jldoctest run
julia> (outputs_sim[:var4],outputs_sim[:var6])
([12.0], [41.95])
```
