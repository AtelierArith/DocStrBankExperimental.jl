```julia
nanaad(A; dims)
```

平均（平均）絶対偏差は、`NaN`を無視して、インデックス可能なコレクション`A`から計算され、オプションで`dims`で指定された次元に沿って計算されます。正規分布の場合、sigma = 1.253 * AADであることに注意してください。

また、`dim`キーワードもサポートされており、`dims`と同様に動作しますが、削減された任意のシングルトン次元をドロップします（これは他のいくつかの言語での慣例です）。
