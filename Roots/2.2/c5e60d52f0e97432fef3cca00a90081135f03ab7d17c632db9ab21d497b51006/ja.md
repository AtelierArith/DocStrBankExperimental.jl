```
Steffensen()
```

二次収束する[Steffensen](https://en.wikipedia.org/wiki/Steffensen's_method#Simple_description)法は、導関数を必要としない`Order2()`アルゴリズムに使用されます。二次収束するニュートン法とは異なり、導関数は必要ありませんが、ニュートン法と同様に、ステップごとに2回の関数呼び出しが必要です。Steffensenのアルゴリズムは、`f(x)`が大きいときに`f'(x)`の近似方法のため、ニュートン法よりも不良な初期推測に対して敏感です。`Order2`メソッドは、`f(x)`が大きいときにSteffensenステップをセカントステップに置き換えます。

誤差`eᵢ - α`は、`eᵢ₊₁ = f[xᵢ, xᵢ+fᵢ, α] / f[xᵢ,xᵢ+fᵢ] ⋅ (1 - f[xᵢ,α] ⋅ eᵢ²`を満たします。
