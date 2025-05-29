**Base64 インターフェース**

### base64img(name::String, raw::Any, filetype::String = "png") -> ::Component

---

任意のタイプから Base64 画像コンポーネントを作成し、画像/**filetype** MIME で表示します。例えば、png としてのみ表示されるプロットです。

#### 例

```
function serveb64(c::Connection)
      # このコンテンツは Julia 画像またはプロットである可能性があります。この例では
      #    julia_img が PNG Julia 画像であると仮定します。
      image = base64img(julia_img, "png")
      write!(c, image)
end
```
