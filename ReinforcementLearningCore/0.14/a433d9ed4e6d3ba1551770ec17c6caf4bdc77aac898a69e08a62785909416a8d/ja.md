```
RandomPolicy(action_space=nothing; rng=Random.default_rng())
```

`action_space`が`nothing`の場合、ランタイムで`legal_action_space`を使用してランダムにアクションを選択します。それ以外の場合は、`action_space`内のランダムな要素が選択されます。

!!! note
    `FULL_ACTION_SET`の環境を扱うときは、常に`action_space=nothing`を設定するべきです。

