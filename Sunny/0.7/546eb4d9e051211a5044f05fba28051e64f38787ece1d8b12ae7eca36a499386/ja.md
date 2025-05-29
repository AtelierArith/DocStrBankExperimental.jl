```
standardize(cryst::Crystal; idealize=true)
```

対称性に基づいて標準化された結晶単位格子を返します。`idealize=true`の場合、格子ベクトルとサイト位置が調整されます。詳細については、[spglib documentation](https://spglib.readthedocs.io/en/stable/)の「定義と規約」を参照してください。
