`@with_kw`と同様ですが、再定義警告を避けるために`show`メソッドを定義しません。

```julia
@with_kw_noshow struct MM{R}
    r::R = 1000.
    a::Int = 4
end
```

詳細についてはマニュアルを参照してください。
