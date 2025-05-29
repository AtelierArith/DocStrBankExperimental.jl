**セッションインターフェース**

### kill!(c::Connection, event::AbstractString) -> _

---

接続のセッションから指定されたイベントコールを削除します。

#### 例

```
route("/") do c::Connection
    myp = p("hello", text = "wow")
    on(c, "load") do cm::ComponentModifier
        set_text!(cm, myp, "not so wow")
    end
    write!(c, myp)
end
```
