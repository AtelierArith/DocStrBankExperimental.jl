```
throw_error(::OnlySingleQubitNoiseInUseError)
```

2量子ビットまたは複数の量子ビットノイズがテストされていない場合にエラーをスローします。

# 例

```julia
throw_error(OnlySingleQubitNoiseInUseError()) # "2量子ビットまたは複数の量子ビットノイズがテストされておらず、実行を許可されるまで"というメッセージでエラーをスローします。
```
