```
iterated_dominance_frontier(cfg::CFG, liveness::BlockLiveness, domtree::DomTree)
    -> phinodes::Vector{Int}
```

反復支配フロンティアを実行します。ここにあるアルゴリズムは基本的にLLVMに従っており、LLVM自体は[^\SG95]で説明されている線形時間アルゴリズムのクリーンアップ版です。

ここにあるアルゴリズムは非常に簡単です。CFGがあると仮定しましょう：

```
A -> B -> D -> F
 \-> C ------>/
```

および対応する支配木：

```
A
|- B - D
|- C
|- F
```

さて、スロットの定義ごとに、単に支配木を下って、定義に根ざした部分木から出るエッジを探します。

上の例では、`B`に定義がある場合、その後継である`D`を見ます。`D`は`B`に支配されているため、ϕノードは必要ありません。次に、`B`に根ざした部分木を下り、`D`に到達します。`D`には後継`F`があり、これは現在の部分木の一部ではないため（つまり、`B`に支配されていないため）、ϕノードが必要です。

このアルゴリズムの重要な洞察は、ブロック`A`と`B`に2つの定義があり、`A`が`B`を支配している場合、`B`に再帰する必要がないということです。なぜなら、`B`に根ざした部分木から外部への潜在的な逆エッジの集合は、`A`に根ざした部分木から外部への逆エッジの集合の厳密な部分集合だからです。ただし、これは逆方向には機能しないことに注意してください。したがって、アルゴリズムは常に`A`の前に`B`を訪れることを確認する必要があります。

[^SG95]: Vugranam C. Sreedhar and Guang R. Gao. 1995.      A linear time algorithm for placing φ-nodes.      In Proceedings of the 22nd ACM SIGPLAN-SIGACT symposium on Principles of programming languages (POPL '95).      Association for Computing Machinery, New York, NY, USA, 62–73.      DOI: [https://doi.org/10.1145/199448.199464](https://doi.org/10.1145/199448.199464).
