```
numberOfAlms(lmax::Integer, mmax::Integer) -> Integer
numberOfAlms(lmax::Integer) -> Integer
```

指定された範囲の ℓ および m に対して a_ℓm 係数を格納するために必要な複素数の配列のサイズを返します。`mmax` が指定されていない場合、それは `lmax` と等しいと見なされます。`lmax` と `mmax` が矛盾しているか負の値の場合、`DomainError` 例外がスローされます。
