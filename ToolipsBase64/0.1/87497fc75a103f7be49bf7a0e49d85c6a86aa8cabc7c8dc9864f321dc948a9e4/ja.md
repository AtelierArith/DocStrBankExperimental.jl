**Base64 インターフェース**

### update_base64!(cm::ComponentModifier, name::String, raw::Any, filetype::String = "png") -> ::Component

---

指定された名前の img コンポーネントを Base64 の生ソースで更新します。

#### 例

```julia
function serveb64(c::Connection)
      # このコンテンツは Julia 画像またはプロットである可能性があります。この例では
      #    julia_img が PNG Julia 画像であると仮定します。
      image = base64img("myimage", julia_img, "png")
      on(c, image, "click") do cm::ComponentModifier
            update_base64!(cm, "image", other_julia_img, "png")
      end
      write!(c, image)
end
```
