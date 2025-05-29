```
@forward T.x functions...
```

型 `T` に対して `functions` のメソッドを定義し、フィールド `x` の関連する関数を呼び出します。

# 例

```julia
struct Wrapper
    x
end

@forward Wrapper.x  Base.sqrt                                  # これで sqrt(Wrapper(4.0)) == 2.0 になります
@forward Wrapper.x  Base.length, Base.getindex, Base.iterate   # 複数の転送された関数がタプルに入れられます
@forward Wrapper.x (Base.length, Base.getindex, Base.iterate)  # 上記と同等です
```
