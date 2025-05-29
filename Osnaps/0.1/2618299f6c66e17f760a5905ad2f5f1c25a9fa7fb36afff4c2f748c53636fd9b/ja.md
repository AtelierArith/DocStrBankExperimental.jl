```
minimize!(o::GenericMinimizer, fn::Function, lb::NTuple{ND}, ub::NTuple{ND}; itmax::Int=210*ND, dmax::Real=1e-7, avgtimes::Int=1)
```

「グローバル」最小化を進めるためのインターフェース関数です。

## 引数:

  * `o`:        `minimizer(..., method="global")`によって作成された最小化のためのオブジェクト。
  * `fn`:       最小化される目的関数。              `fn`は`fn(x::Vector)`の1つの引数で呼び出せる必要があります。              追加の引数を渡す必要がある場合は、              `fcall(fn, x) = fn(x; kwargs...)`で関数をディスパッチしてください。
  * `lb`:       実現可能であることが強制される最小化の下限。
  * `ub`:       実現可能であることが強制される最小化の上限。
  * `itmax`:    最小化の反復の最大数（*オプション*）。
  * `dmax`:     局所的最小値に陥るのを防ぐための基準として作用するユークリッド距離（*オプション*）。
  * `avgtimes`: 全体の最小化プロセスの平均回数（*オプション*）。
