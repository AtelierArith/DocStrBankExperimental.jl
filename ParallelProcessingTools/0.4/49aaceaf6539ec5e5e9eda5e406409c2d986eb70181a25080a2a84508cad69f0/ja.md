```
struct AutoThreadPinning
```

ParallelProcessingTools のデフォルトスレッドピンニングモード。

コンストラクタ:

```julia
AutoThreadPinning(; random::Bool = false, pin_blas::Bool = false)
```

引数:

  * `random`: スレッドアフィニティマスクが設定されていない場合（例: SLURM や `taskset` を介して）、システムトポロジーに基づくランダムスレッドピンニングを使用します。
  * `blas`: BLAS スレッドをピン留めしようとします。BLAS スレッドピンニングのバグのため完全には機能しません（ThreadPinning の問題 [#105](https://github.com/carstenbauer/ThreadPinning.jl/issues/105) を参照）。

`ThreadPinning.pinthreads` と一緒に使用します:

```julia
using ParallelProcessingTools, ThreadPinning
pinthreads(AutoThreadPinning())
```
