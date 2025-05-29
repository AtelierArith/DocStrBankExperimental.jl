```
RandomPolicy{RNG<:AbstractRNG, P<:Union{POMDP,MDP}, U<:Updater}
```

アクション関数を使用してアクションのリストを作成し、そこからランダムにアクションをサンプリングする一般的なポリシーです。

コンストラクタ:

```
`RandomPolicy(problem::Union{POMDP,MDP};
         rng=Random.default_rng(),
         updater=NothingUpdater())`
```

# フィールド

  * `rng::RNG` ランダム数生成器
  * `probelm::P` POMDPまたはMDPの問題
  * `updater::U` 信念のアップデータ（上記のコンストラクタではデフォルトで`NothingUpdater`）
