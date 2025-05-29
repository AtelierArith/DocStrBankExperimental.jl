```
Order5()
KumarSinghAkanksha()
```

*非線形方程を解くための新しい5次導関数フリー・ニュートン型法*に基づく5次アルゴリズムを実装します。著者はManoj Kumar、Akhilesh Kumar Singh、Akankshaで、Appl. Math. Inf. Sci. 9, No. 3, 1507-1513 (2015)、DOI: [10.12785/amis/090346](https://doi.org/10.12785/amis/090346)です。ステップごとに4回の関数呼び出しが必要です。`Order5`メソッドは、`f(x)`が大きいときにSteffensenステップをセカントステップに置き換えます。

誤差`eᵢ = xᵢ - α`は、`eᵢ₊₁ = K₁ ⋅ K₅ ⋅ M ⋅ eᵢ⁵ + O(eᵢ⁶)`を満たします。
