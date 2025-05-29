```
Clp_loadProblem(model, numcols, numrows, start, index, value, collb, colub, obj, rowlb, rowub)
```

問題を読み込みます（行の制約は下限と上限によって与えられます）。ポインタがNULLの場合、次の値はデフォルトになります: <ul> <li> <code>colub</code>: すべての列の上限は無限大 <li> <code>collb</code>: すべての列の下限は0 <li> <code>rowub</code>: すべての行の上限は無限大 <li> <code>rowlb</code>: すべての行の下限は-無限大 <li> <code>obj</code>: すべての変数の目的係数は0 </ul>

他のloadProblem()メソッドと同様ですが、行列は標準の列優先順序形式（ギャップなし）で与えられます。
