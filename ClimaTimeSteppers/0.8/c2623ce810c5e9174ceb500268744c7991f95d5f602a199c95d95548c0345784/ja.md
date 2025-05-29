```
JacobianFreeJVP
```

ニュートン-クライロフ法のために、ヤコビ行列 `j(x[n])` を直接使用することなく、`j(x[n]) * Δx[n]` のヤコビ行列-ベクトル積を計算します。代わりに、`x[n]`、`f(x[n])`、および他の関数評価 `f(x′)` のみを使用します。これは、`jvp!(::JacobianFreeJVP, cache, jΔx, Δx, x, f!, f, prepare_for_f!)` を呼び出すことによって行われます。ヤコビ行列フリーの JVP に渡される `jΔx` は、インプレースで修正されます。`cache` は、`allocate_cache(::JacobianFreeJVP, x_prototype)` を使用して取得でき、ここで `x_prototype` は `x`（および `Δx` と `f` にも）に似ています。
