```
MCMCOptionsList(;
numiters = 5000,
burnin = floor(0.2 * numiters),
thin = 1,
numGibbs = 5,
numMH = 1)

MCMCを実行するためのオプションのリスト。

# コンストラクタ引数
- `numiters::Integer`: 実行する反復回数。
- `burnin::Integer`: バーンインとして破棄する反復回数。
- `thin::Integer`: `thin` サンプルごとに保持します。
- `numGibbs:Integer`: スプリット-マージステップでの中間ギブススキャンの数。
- `numMH:Integer`: MCMC反復ごとのスプリット-マージステップの数。
```
