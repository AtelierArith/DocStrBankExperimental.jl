```
sample_type(x)
```

`x.sample_type`を`Onda.LPCM_SAMPLE_TYPE_UNION`のサブタイプとして返します。もし`x.sample_type`がOnda指定の`sample_type`文字列（例: `"int16"`）であれば、それは対応するJulia型に変換されます。もし`x.sample_type <: Onda.LPCM_SAMPLE_TYPE_UNION`であれば、この関数は単に`x.sample_type`をそのまま返します。
