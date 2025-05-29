```
train!(gen_fn::GenerativeFunction, data_generator::Function,
       update::ParamUpdate,
       num_epoch, epoch_size, num_minibatch, minibatch_size; verbose::Bool=false)
```

与えられた生成関数を訓練して、`gen_fn` が入力に対して割り当て `constraints` を生成する際の期待条件付き対数確率（密度）を最大化します。この期待値は、`data_generator` の出力分布の下で取られます。

関数 `data_generator` は引数を持たない関数で、`inputs` が `gen_fn` への入力（引数）のタプルであり、`constraints` が `ChoiceMap` であるタプル `(inputs, constraints)` を返します。

`conf` は使用される最適化アルゴリズムを設定します。

`param_lists` は生成関数からそのパラメータのリストへのマップです。これは、データ生成器の条件付き分布 `constraints | inputs` から生成関数によって表される分布への期待KLダイバージェンスを最小化することに相当します。この期待値は、データ生成器によって決定される `inputs` の周辺分布の下で取られます。
