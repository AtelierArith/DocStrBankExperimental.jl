```
@color_output enabled::Bool expr
```

指定された式のカラー印刷を有効または無効にします。しばしば `@capture_*` マクロと組み合わせて使用するのに便利です。

## 例

@color*output false begin     output = @capture*err begin         @warn "キャプチャされるべきで、印刷されるべきではない"     end end @test output == "WARNING: キャプチャされるべきで、印刷されるべきではない "
