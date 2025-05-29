```
meq(exp)
```

関数を展開するためのマクロ `t[d1 in dim1, d2 in dim2, dfix,..] = value`

このマクロを使うことで、次のように記述することができます：

```
@meq par1[d1 in DIM1, d2 in DIM2, dfix3] =  par2[d1,d2]+par3[d1,d2]
```

そして得られる結果は：

```
[par1[d1,d2,dfix3] =  par2[d1,d2]+par3[d1,d2] for d1 in DIM1, d2 in DIM2]
```

つまり、「モデル方程式」を簡潔で読みやすい方法で記述することが可能です。
