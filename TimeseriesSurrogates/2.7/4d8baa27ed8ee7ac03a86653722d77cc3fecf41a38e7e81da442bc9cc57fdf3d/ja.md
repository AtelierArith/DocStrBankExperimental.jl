```
BlockShuffle(n::Int; shift = false)
```

時間系列をほぼ等しい幅の `n` ブロックにランダムなインデックスで分割することによって構築されたブロックシャッフルサロゲート（終端ブロックは時間系列の開始にラップされます）。

`shift` が `true` の場合、ブロックを選択する前に入力信号がランダムなステップ数だけ円形にシフトされます。

ブロックシャッフルサロゲートは、時間系列の短期的な時間的特性（例えば、ブロック長よりも短い遅延での相関）を大まかに保持しますが、長期的な動的情報（例えば、ブロック長を超える相関）を破壊します。

したがって、これらのサロゲートは、信号の短期的な動的特性と長期的な動的特性を比較することを目的とした帰無仮説をテストするために使用できます。
