```
ustrip(A::Diagonal)
ustrip(A::Bidiagonal)
ustrip(A::Tridiagonal)
ustrip(A::SymTridiagonal)
```

さまざまな種類の行列から単位を削除するには、基になるベクトルに対して `ustrip` を呼び出します。
