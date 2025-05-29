```
load_bz(::IBZ, A, B, species::AbstractVector, positions::AbstractMatrix; kws...)
```

`species` は各原子タイプに対して異なるラベルを持っている必要があります（例えば、任意の文字列または整数）。`positions` は、対応する種の原子の座標を与える列を持つ行列でなければなりません。
