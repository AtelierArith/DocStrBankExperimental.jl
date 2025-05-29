**セッションインターフェース**

### kill!(c::Connection)

---

接続の保存されたイベントを終了します。

#### 例

```
using Toolips
using ToolipsSession

route("/") do c::Connection
    on(c, "load") do cm::ComponentModifier
        alert!(cm, "このテキストは決して表示されません。")
    end
    println(length(keys(c[:Session].iptable)))
    kill!(c)
    println(length(keys(c[:Session].iptable)))
end
```
