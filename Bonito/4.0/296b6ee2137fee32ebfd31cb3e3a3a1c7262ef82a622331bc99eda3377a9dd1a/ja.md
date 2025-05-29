```
Grid(
    elems...;
    gap="10px",
    width="100%",
    height="100%",
    # 以下の属性はデフォルトのCSS値に設定されています：
    columns="none",
    rows="none",
    areas="none",
    justify_content="normal",
    justify_items="legacy",
    align_content="normal",
    align_items="legacy",
    style::Styles=Styles(),
    div_attributes...,
)
```

グリッドは、強力なCSS `display: grid`プロパティに基づいて、その子要素をグリッドにレイアウトするコンテナです。
