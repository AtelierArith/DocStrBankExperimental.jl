```julia
VectorContinuousCallback(condition,affect!,affect_neg!,len;
                         initialize = INITIALIZE_DEFAULT,
                         finalize = FINALIZE_DEFAULT,
                         idxs = nothing,
                         rootfind=LeftRootFind,
                         save_positions=(true,true),
                         interp_points=10,
                         abstol=10eps(),reltol=0,repeat_nudge = 1//100)
```

```julia
VectorContinuousCallback(condition,affect!,len;
                   initialize = INITIALIZE_DEFAULT,
                   finalize = FINALIZE_DEFAULT,
                   idxs = nothing,
                   rootfind=LeftRootFind,
                   save_positions=(true,true),
                   affect_neg! = affect!,
                   interp_points=10,
                   abstol=10eps(),reltol=0,repeat_nudge=1//100)
```

これは `AbstractContinuousCallback` のサブタイプでもあります。多くのコールバックがある場合、`CallbackSet` はスケーラビリティが悪いため、実用的ではありません。この理由から、`VectorContinuousCallback` が用意されています - これは複数のイベントに対して単一のコールバックを持つことを可能にします。

# 引数

  * `condition`: これは関数 `condition(out, u, t, integrator)` で、適切なインデックスで配列 `out` に条件値を保存する必要があります。`out` の最大インデックスはコールバックの `len` プロパティで指定する必要があります。このようにして、`len` のイベントのチェーンを持つことができ、`out[i] = 0` のときに `i` 番目のイベントがトリガーされます。
  * `affect!`: これは関数 `affect!(integrator, event_index)` で、`integrator` を修正することを可能にし、`event_idx` を使用してどのイベントが発生したかを知らせます。つまり、`out[i]` がゼロになったインデックス `i` を提供します。
  * `len`: チェーンされたコールバックの数。これは必須で指定する必要があります。

残りの引数は [`ContinuousCallback`](@ref) と同じ意味を持ちます。
