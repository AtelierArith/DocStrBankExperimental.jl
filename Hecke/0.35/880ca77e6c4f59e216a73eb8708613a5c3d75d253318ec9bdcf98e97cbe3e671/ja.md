```
genus(HermLat, E::NumField, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, data::Vector; type::Symbol = :det,
	                                           check::Bool = true)
                                                             -> HermLocalGenus
```

代数 `E` 上のエルミート格子のための局所属符号 `g` を、基底体 $K$ において、$\mathcal O_K$ の素イデアル `p` で構成します。その不変量は `data` によって指定されます。

  * 素イデアルが良い場合（分岐せず二重でない場合）、`data` の要素は `(s, r, d)::Tuple{Int, Int, Int}` でなければならず、ここで `s` はスケール $\mathfrak P$-評価、`r` は階数、`d` は `g` のジョルダンブロックの行列式/判別式類を指します。ここで、$\mathfrak P$ は `p` の上にある $\mathcal O_E$ の素イデアルです。

    非分岐の場合、`d` は `s` と `r` によって決定され、省略可能です。したがって、`(s, r)::Tuple{Int, Int}` も許可されます。
  * 素イデアルが悪い場合（分岐しており二重である場合）、`data` の要素は `(s, r, d, n)::Tuple{Int, Int, Int, Int}` でなければならず、さらに `n` はノルム `p`-評価を指します。

追加のコメント：

  * `d` は $\{[1, -1\}$ に属さなければなりません；
  * `type == :disc` の場合、パラメータ `d` は判別式として解釈されます；
  * 整合性チェックは `check == false` に設定することで無効にできます。
