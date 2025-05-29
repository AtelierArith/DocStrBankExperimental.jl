```
tag(tag_name, args...)
```

指定された `tag_name` と `args` に指定された属性/コンテンツ/ネストされたタグを持つ HTML タグを生成します。

## 例

### 基本的な使い方

```julia
# コンテンツを持つ <h1> タグを生成
println(tag("h1", "Hello, World!"))  
# 出力: "<h1>Hello, World!</h1>"

# クラス属性とコンテンツを持つ <p> タグを生成
println(tag("p", :class => "text-lg", "This is a paragraph."))  
# 出力: "<p class="text-lg">This is a paragraph.</p>"
```

### ネストされたタグ

```julia
# ネストされた <p> と <span> タグを持つ <div> を生成
println(tag("div", tag("p", "A paragraph."), tag("span", "A span.")))  
# 出力: "<div><p>A paragraph.</p><span>A span.</span></div>"
```

### 特殊属性

```julia
# カスタム属性を持つ <var> タグを生成
println(tag("var", :data_value => "42", "x"))  
# 出力: "<var data-value="42">x</var>"
```

### 属性、コンテンツ、ネストされたタグの混合

```julia
# href 属性、クラス属性、コンテンツを持つ <a> タグを生成
println(tag("a", :href => "https://example.com", :class => "link", "Visit Example"))  
# 出力: "<a href="https://example.com" class="link">Visit Example</a>"
```

## 注意事項

  * `tag_name` は HTML タグ名を表す文字列である必要があります（例: "div", "span", "h1"）。
  * `args` は以下の混合が可能です：
  * 属性のペア（例: `:class => "text-lg"`)
  * コンテンツの文字列（例: `"Hello, World!"`）
  * ネストされたタグのための関数（例: `tag("p", "A paragraph.")`）
