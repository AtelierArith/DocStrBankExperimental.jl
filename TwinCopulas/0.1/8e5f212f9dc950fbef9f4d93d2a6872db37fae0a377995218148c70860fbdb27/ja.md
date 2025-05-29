```
ArchimaxCopula{A, E}
```

フィールド:

```
-Archimedean::A - アルキメデアンコピュラ
-Extreme::E - 極値コピュラ
```

コンストラクタ

```
ArchimaxCopula(Archimedean, Extreme)
```

二変量アルキマックスコピュラは、アルキメデアンコピュラと極値コピュラによってパラメータ化されます。次のように構築されます:

$$
C_{\ell, \varphi}(u_1, u_2) = \varphi(\ell(\varphi^{-1}(u_1),\varphi^{-1}(u_2)))
$$

ここで、$\varphi$はアルキメデアンコピュラの生成関数であり、$\varphi^{-1}$はその逆で、$\ell$は極値コピュラの安定した尾部依存関数です。

詳細については、次を参照してください。

参考文献:

  * [Charpentier2014](@cite) Charpentier et al, Multivariate Archimax Copulas, Journal of Multivariate analysis. 2014.
