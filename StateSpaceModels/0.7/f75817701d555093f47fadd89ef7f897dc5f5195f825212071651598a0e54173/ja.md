```
isfitted(model::StateSpaceModel) -> Bool
```

`model`がフィッティングされているかを確認します。すなわち、ハイパーパラメータに少なくとも1つの`NaN`エントリがある場合は`false`を返します。
