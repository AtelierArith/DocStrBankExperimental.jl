```
factorize!(mumps)
```

`Mumps` インスタンスに登録された行列を因数分解します。行列は `associate_matrix()` で事前に登録されている必要があります。因数分解後、要求された場合、行列式は `mumps.det` に保存されます。MUMPS エラーコードは `mumps.err` に保存されます。
