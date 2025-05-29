```
getproperty(@nospecialize(ids::IDS), field::Symbol, @nospecialize(default::Any); to_cocos::Int=user_cocos)
```

要求されたフィールドのIDS値を返すか、フィールドが欠落している場合は`default`を返します

注意: これは、IDS内の`missing`フィールドにアクセスするとエラーが発生するため、有用です
