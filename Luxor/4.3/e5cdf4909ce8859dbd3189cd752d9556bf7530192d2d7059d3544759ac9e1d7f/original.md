```
settext(text, pos;
    halign = "left",
    valign = "bottom",
    angle  = 0, # degrees!
    markup = false)

settext(text;
    kwargs)
```

Draw the `text` at `pos` (if omitted defaults to `0/0`). If no font is specified, on macOS the default font is Times Roman.

To align the text, use `halign`, one of "left", "center", or "right", and `valign`, one of "top", "center", or "bottom".

`angle` is the rotation - in counterclockwise degrees, rather than Luxor's default clockwise (+x-axis to +y-axis) radians.

If `markup` is `true`, then the string can contain some HTML-style markup. Supported tags include:

`<b>`, `<i>`, `<s>`, `<sub>`, `<sup>`, `<small>`, `<big>`, `<u>`, `<tt>`, and `<span>`

The `<span>` tag can contains things like this:

```
<span font='26' background='green' foreground='red'>unreadable text</span>
```
