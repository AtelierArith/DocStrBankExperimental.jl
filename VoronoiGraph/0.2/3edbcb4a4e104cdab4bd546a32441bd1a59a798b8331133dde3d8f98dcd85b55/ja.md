```
mc_integrate(f::Function, i::Int, xs::Points, nmc=1000, nmc2=1000, searcher=Raycast(xs))
```

関数 `f` をセル `i` とその境界で積分し、体積積分のためにセルごとに `nmc` 本の光線と光線ごとに `nmc2` 点を使用します。

# 戻り値:

  * `Vf::Real`: `f` の体積積分
  * `Af::SparseVector`: Af[j] はセル i と j の交差部分における `f` の表面積分です。
  * `V::Real`: セル `i` の体積
  * `A::SparseVector`: A[j] はセル i と j の交差部分の表面積です。

```
