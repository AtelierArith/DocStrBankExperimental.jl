```
select(
    bibliography::DataStructures.OrderedDict{String,Entry},
    selection::Vector{String};
    complementary::Bool = false
    )
```

与えられた選択キーのセットに基づいて文献の一部を選択します。complementaryがtrueの場合、selectionは保持されないエントリを指定します。デフォルトでは、complementaryはfalseに設定されています。
