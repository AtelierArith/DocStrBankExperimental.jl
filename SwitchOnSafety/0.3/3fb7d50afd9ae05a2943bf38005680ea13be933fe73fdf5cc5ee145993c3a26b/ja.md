```
soslyapb(s::AbstractSwitchedSystem, d::Integer;
         verbose=0, tol=1e-5, step=0.5, scaling=quickub(s),
         ranktols=tol, disttols=tol, kws...)
```

制約付きジョイントスペクトル半径の上限を見つけます [(5), PJ08]。下限は[LPJ19]の保証を使用して得られます。

[LPJ19] B. Legat, P. A. Parrilo and R. M. Jungers *スイッチドシステムの計算複雑性に対するエントロピーに基づく境界*. IEEE Transactions on Automatic Control, **2019**.

[PJ08] P. Parrilo and A. Jadbabaie. *二次和を用いたジョイントスペクトル半径の近似*. Linear Algebra and its Applications, Elsevier, **2008**, 428, 2385-2402
