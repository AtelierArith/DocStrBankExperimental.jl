```
certify_patchwork(F::System; Number_Real_Solutions = false)
```

与えられたシステムがパッチワークされているかどうかを認証し、すべての実数解が実多面体ホモトピーを使用して見つけられることを確認します。システム `F` が認証不等式に従ってパッチワークされていると認証される場合、値 `1` が返されます。そうでない場合は `0` が返されます。

# 引数

  * `F` : 実多面体ホモトピーの対象システム。

```julia
@var x y;
F = System([-1 - 24000*y + x^3, -9 + 50*x*y - 1*y^2]);
result = certify_patchwork(F)
```

```
1
```

  * オプション `Number_Real_Solutions` があり、対象システムがパッチワークされている場合に `(1,k)` を返します。ここで `k` は対象システムの実数解の数です。オプションのデフォルト値は false です。

```julia
result = certify_patchwork(F; Number_Real_Solutions = true)
```

```
(1,4)
```
