```
integrate_material!(material::GenericChaboche{T}) where T <: Real
```

二つのバックストレスを持つシャボッシュ材料。運動硬化と等方硬化の両方。

参照：

```
J.-L. Chaboche. 循環塑性および循環粘塑性のための構成方程式。国際塑性学ジャーナル 5(3) (1989), 247--302.
https://doi.org/10.1016/0749-6419(89)90015-6
```

さらなる読み物：

```
J.-L. Chaboche. 一部の塑性および粘塑性構成理論のレビュー。国際塑性学ジャーナル 24 (2008), 1642--1693.
https://dx.doi.org/10.1016/j.ijplas.2008.03.009

J.-L. Chaboche, A. Gaubert, P. Kanouté, A. Longuet, F. Azzouz, M. Mazière.
循環硬化と動的ひずみ老化を含む燃焼室材料の粘塑性構成方程式。国際塑性学ジャーナル
46 (2013), 1--22. https://dx.doi.org/10.1016/j.ijplas.2012.09.011
```
