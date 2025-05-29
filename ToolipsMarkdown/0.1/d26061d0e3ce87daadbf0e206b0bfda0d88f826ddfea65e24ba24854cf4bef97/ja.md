**Toolips Markdown**

### tmd(name::String = "tmd", s::String = "") -> ::Component

---

Markdown文字列をToolipsコンポーネントに変換します。Markdownは常にデフォルトスタイルを使用します。

#### 例

```
route("/") do c::Connection
    mymdcomp = tmd("mainmarkdown", "# こんにちは！ [クリック](http://toolips.app/)")
    write!(c, mymdcomp)
end
```
