```
Phases = Union{CreateState, SaveState, LoadState, ToMixed, Evolve, Gates, Dmrg, PartialTrace, SteadyState}
```

SimDataおよびrunTMSのためのすべての可能なフェーズタイプを含む型です。各タイプには、少なくとも以下の3つのフィールドが含まれています（SimDataのように）。

  * `name`: フェーズの名前
  * `time_start`: フェーズの開始時に使用するシミュレーション時間
  * `final_measures`: フェーズの終了時に行う測定、`measure`および`output`を参照してください。
