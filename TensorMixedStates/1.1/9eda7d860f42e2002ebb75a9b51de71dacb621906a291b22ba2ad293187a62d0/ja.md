```
Phases = Union{CreateState, SaveState, LoadState, ToMixed, Evolve, Gates, Dmrg, PartialTrace, SteadyState}
```

SimDataとrunTMSのためのすべての可能なフェーズタイプを含む型です。各タイプは、少なくとも以下の3つのフィールドを含んでいます（SimDataのように）。

  * `name`: フェーズの名前
  * `time_start`: フェーズの開始時に使用するシミュレーション時間
  * `final_measures`: フェーズの終了時に行う測定、`measure`および`output`を参照してください。
