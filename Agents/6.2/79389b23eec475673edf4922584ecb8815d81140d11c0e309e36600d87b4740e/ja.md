```
interacting_pairs(model, r, method; scheduler = abmscheduler(model)) → piter
```

近接するエージェントの**ユニークなペア** `(a, b)` を返すイテレータを返します。これらのエージェントは、相互作用半径 `r` 内にあります。

この関数は、すべての近接エージェントのペア間で一度だけペアワイズ相互作用を行いたい場合に `model_step!` と組み合わせて使用すると便利です（`agent_step!` を使用すると、`a` と `b` の両方でイベントが2回トリガーされるため、これを避けたい場合）。つまり、ペア `(a, b)` が存在する場合、ペア `(b, a)` はイテレータに含まれません！

イテレータからペアIDのベクターを取得するには `piter.pairs` を使用します。

引数 `method` は3つのペアリングシナリオを提供します。

  * `:all`: 半径 `r` 内にあるすべてのエージェントのペアを返します。最も近いものだけではありません。
  * `:nearest`: エージェントは、半径 `r` 内に存在する真の最近接隣人とだけペアになります。各エージェントは1つのペアにしか属することができないため、2つのエージェントが同じ最近接隣人を共有する場合、距離でソートされた後、`scheduler` の次のIDによって1つだけがペアになります。
  * `:types`: 混合エージェントモデルのみ。半径 `r` 内のすべてのエージェントのペアを返します（`:all` に似ていますが、異なるタイプのペアのみをキャプチャします）。例えば、`Union{Sheep,Wolf}` のモデルは `(Sheep, Wolf)` のペアのみを返します。複数のエージェントタイプ、例えば `Union{Sheep, Wolf, Grass}` の場合、`Grass` を含むペアをスキップするには、`Grass` タイプをスケジュールしない [`scheduler`](@ref Schedulers) を使用することで実現できます。すなわち、`scheduler(model) = (a.id for a in allagents(model) if !(a isa Grass))` のようにします。

以下のキーワードを使用できます。

  * `scheduler = abmscheduler(model)` は、ペアを見つけるためのイテレーション中にエージェントをスケジュールします。特に `:nearest` の場合、エージェントの順序が異なると異なる結果が得られるため、重要です（`b` が `a` の最近接エージェントであるが、`a` が `b` の最近接エージェントでない場合、ペア `(a, b)` を取得できるかどうかは、`a` が最初にスケジュールされたかどうかに依存します）。
  * `search = :exact` は、`:all, :types` の場合に近くのIDを見つける方法を決定します。`:exact` または `:approximate` でなければなりません。

[Bacterial Growth](https://juliadynamics.github.io/AgentsExampleZoo.jl/dev/examples/growing_bacteria/) モデルでの使用例。

!!! note "CellListMap.jl でのパフォーマンス向上"
    [`interacting_pairs`](@ref) が有用なほとんどのアプリケーションでは、CellListMap.jl と統合することで大幅な（10倍から100倍の）パフォーマンス向上が得られます。これを行う方法については、[CellListMap.jl と Agents.jl の統合例](@ref) をチェックしてください。

