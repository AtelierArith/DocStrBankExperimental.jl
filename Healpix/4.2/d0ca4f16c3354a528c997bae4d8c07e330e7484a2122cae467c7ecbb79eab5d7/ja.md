```
npix2nside(npix::Integer) -> Integer
```

ヒールピクセルマップのピクセル数を与えると、`NSIDE` 解像度パラメータを返します。数が無効な場合は、`DomainError` 例外をスローします。
