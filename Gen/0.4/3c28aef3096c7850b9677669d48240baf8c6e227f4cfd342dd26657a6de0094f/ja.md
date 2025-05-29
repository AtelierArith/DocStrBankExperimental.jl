```
(log_incremental_weights,) = particle_filter_step!(
    state::ParticleFilterState, new_args::Tuple, argdiffs,
    observations::ChoiceMap, proposal::GenerativeFunction, proposal_args::Tuple)
```

粒子フィルタの更新を行います。ここでは、モデルの引数が調整され、新しい観測が追加され、カスタム提案とモデルの内部提案の組み合わせが新しい潜在状態を提案するために使用されます。つまり、各粒子について、

  * 提案関数 `proposal` は引数 `Tuple(t_old, proposal_args...)`（ここで `t_old` は古いモデルトレース）で評価され、自身のトレース（これを `proposal_trace` と呼びます）を生成します。そして
  * 古いモデルトレースは新しいモデルトレース（これを `t_new` と呼びます）に置き換えられます。

`t_new` の選択マップは以下の条件を満たします：

1. `get_choices(t_old)` は `get_choices(t_new)` の部分集合である；
2. `observations` は `get_choices(t_new)` の部分集合である；
3. `get_choices(proposal_trace)` は `get_choices(t_new)` の部分集合である。

ここで、選択マップ `a` が別の選択マップ `b` の「部分集合」であると言うとき、私たちは `a` に現れるすべてのキーが `b` にも現れ、そのアドレスでの値が等しいことを意味します。

上記の条件を満たすトレース `t_new` がモデルのサポート内に存在しない場合はエラーです。そのようなトレースが存在する場合、上記の要件によって決定されないランダムな選択は内部提案を使用してサンプリングされます。
