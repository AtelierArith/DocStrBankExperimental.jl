```
dual(mv::MultiVector)
```

MultiVectorのポアンカレ双対を返します。すべての基底MultiVectorに対して、mv * dual(mv) = 擬スカラーとなります。Dualは線形写像であり、他のMultiVectorの像は基底MultiVectorの像から導かれます。
