```julia
nanminimum(A; dims)
```

`minimum`と同様ですが、`NaN`を無視します：インデックス可能なコレクション`A`の中で、指定された次元`dims`に沿って、最小の非`NaN`値を見つけます。

また、`dim`キーワードもサポートしており、これは`dims`と同様に動作しますが、削減された単一次元をドロップします（これは他のいくつかの言語での慣例です）。
