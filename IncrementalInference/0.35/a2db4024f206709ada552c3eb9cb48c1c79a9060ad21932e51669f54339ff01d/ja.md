```julia
printCSMHistorySequential(hists)
printCSMHistorySequential(hists, whichsteps)
printCSMHistorySequential(hists, whichsteps, fid)

```

hists::Dictのクリックステートマシン履歴の逐次要約行を印刷します。

ノート

  * スライスは許可されています。例を参照してください。

例

```julia
printCSMHistorySequential(hists)
printCSMHistorySequential(hists, 2=>46)
printCSMHistorySequential(hists, 1=>11:15)
printCSMHistorySequential(hists, [1,4,6]=>11:15)
printCSMHistorySequential(hists, [2=>45:52; 1=>10:15])
```

DevNotes

  * TODO いくつかの機能をFSMに移動するかもしれません
  * TODO デフォルトの`whichstep = :=>:`にアップグレードする – すなわち 

      * `(:) |> typeof == Colon`のためのディスパッチを追加する、
      * `5:6=>:`。
  * TODO `Tuple{<:CSMRanges, Pair{<:CSMRanges,<:CSMRanges}}`オプションの間に要素を追加する

      * ([1;3], 1=>5:7)は、CSM 1と3からのすべてのステップを印刷します。これは1=>5と1=>7の間に発生します。
  * TODO もしかしたら`Dict(5=>5:8, 8=>20:25)`、または`Dict(2:5=>[1;3], 10=>1:5)`。

関連:

printHistoryLine, printCliqHistory
