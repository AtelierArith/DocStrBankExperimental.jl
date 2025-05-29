```
Card(
    content;
    style::Styles=Styles(),
    backgroundcolor=RGBA(1, 1, 1, 0.2),
    shadow_size="0 4px 8px",
    padding="12px",
    margin="2px",
    shadow_color=RGBA(0, 0, 0.2, 0.2),
    width="auto",
    height="auto",
    border_radius="10px",
    div_attributes...,
)
```

Cardは影と丸みを帯びた角を持つコンテナです。要素をグループ化し、背景から際立たせる良い方法です。上記のキーワード引数や、任意のCSS属性を持つ`style`引数を通じて、簡単にスタイルを設定できます。

# 例

```@example
    App() do
        Card(
            DOM.h1("これはカードです");
            width="200px",
            height="200px",
            backgroundcolor="white",
            shadow_size="0 0 10px",
            shadow_color="blue",
            padding="20px",
            margin="20px",
            border_radius="20px",
            style = Styles(
                CSS("hover", "background-color" => "lightgray")
            )
        )
    end

```
