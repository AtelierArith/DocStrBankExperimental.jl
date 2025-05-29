フックは、ユーザーがカスタマイズされたランタイムロジックを注入できるように、[`run`](@ref)の異なるステージで呼び出されます。デフォルトでは、`AbstractHook`は何もしません。以下のメソッドを実装することで、動作をカスタマイズできます：

  * `Base.push!(hook::YourHook, ::PreActStage, agent, env)`
  * `Base.push!(hook::YourHook, ::PostActStage, agent, env)`
  * `Base.push!(hook::YourHook, ::PreEpisodeStage, agent, env)`
  * `Base.push!(hook::YourHook, ::PostEpisodeStage, agent, env)`
  * `Base.push!(hook::YourHook, ::PostExperimentStage, agent, env)`

慣例として、`Base.getindex(h::YourHook)`は、私たちが興味のあるメトリクスを抽出するために実装されています。ユーザーは、`+`を使って異なる`AbstractHook`を組み合わせることができます。
