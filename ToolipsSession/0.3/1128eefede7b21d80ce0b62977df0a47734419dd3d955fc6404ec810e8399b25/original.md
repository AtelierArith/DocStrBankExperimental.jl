**Session Interface**

### kill!(c::Connection, event::AbstractString) -> _

---

Removes a given event call from a connection's Session.

#### example

```
route("/") do c::Connection
    myp = p("hello", text = "wow")
    on(c, "load") do cm::ComponentModifier
        set_text!(cm, myp, "not so wow")
    end
    write!(c, myp)
end
```
