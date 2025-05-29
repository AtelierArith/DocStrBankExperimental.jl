```
itsample([rng], iter, method = AlgRSWRSKIP())
itsample([rng], iter, wfunc, method = AlgWRSWRSKIP())
```

イテレータのランダムな要素を返します。オプションで `rng` を指定できます（デフォルトは `Random.default_rng()`）および各要素を入力として受け取り、対応する重みを出力する関数 `wfunc` を指定できます。イテレータが空の場合、`nothing` を返します。

---

```
itsample([rng], iter, n::Int, method = AlgL(); ordered = false)
itsample([rng], iter, wfunc, n::Int, method = AlgAExpJ(); ordered = false)
```

イテレータのランダムな要素のベクトルを `n` 個返します。オプションで `rng`（デフォルトは `Random.default_rng()`）、重み関数 `wfunc`、および `method` を指定できます。`ordered` は、順序付きサンプル（イテレータと同じ順序でアイテムが現れるサンプルとも呼ばれる）を収集する必要があるかどうかを決定します。

イテレータの要素が `n` 未満の場合、置換なしのサンプリングの場合は、それらの要素のベクトルを返します。

---

```
itsample(rngs, iters, n::Int)
itsample(rngs, iters, wfuncs, n::Int)
```

複数のイテラブルからサイズ `n` の置換ありサンプルを返す並列実装です。`n` 以外のすべての引数はタプルでなければなりません。
