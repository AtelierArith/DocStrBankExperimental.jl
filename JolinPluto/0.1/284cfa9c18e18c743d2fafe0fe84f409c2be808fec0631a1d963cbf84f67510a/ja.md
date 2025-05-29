```
Setter()
Setter("initial_value")
```

プルートのインタラクティビティを作成し、セッターセルを状態セルから分離します。

# 使用法

```julia
set_a = Setter("initial_value")

# 別のセルで、セッターから内部状態を抽出します
# そのため、更新がこのセルを再実行します
a = @get set_a

# さらに別のセルで `set_a` を使用します
set_a("new_value")

# または、関数構文を使用して前の値に簡単にアクセスします
set_a() do prev_a
    "$prev_a!!"
end
```
