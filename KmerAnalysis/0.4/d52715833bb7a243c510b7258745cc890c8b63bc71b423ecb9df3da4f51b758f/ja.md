```
KmerFrequencySpectra{2}(xfreqs::Vector{MerCount{M}}, yfreqs::Vector{MerCount{M}}, min_count::Integer = 0) where {M<:AbstractMer}
```

2次元のk-mer頻度スペクトルを、`min_count`を満たさないk-merカウントを除外して、2つのkmerカウントのベクトルから構築します。

!!! tip
    通常、`xfreqs`は大きなデータセットからのカウント、通常は生のリードのようなもので、`yfreqs`は参照ゲノムやゲノムアセンブリグラフのような小さなまたはより圧縮された配列データセットからのカウントであるべきです。

    もし2つの同じサイズのデータセット、例えば2つのリードデータセットを比較している場合、どちらが`xfreqs`として渡され、どちらが`yfreqs`として渡されるかはそれほど重要ではありません。

