```
texttrack(txt, pos, tracking;
    action=:fill,
    halign=:left,
    valign=:baseline,
    startnewpath=true)
texttrack(txt, pos, tracking, fontsize;
    action=:fill,
    halign=:left,
    valign=:baseline,
    startnewpath=true)
```

Place the text in `txt` at `pos`, left-justified, and letter space ('track') the text using the value in `tracking`.

The tracking units depend on the current font size. In a 12‑point font, 1 em equals 12 points. A point is about 0.35mm, 1em is about 4.2mm, and a 1000 units of tracking are about 4.2mm. So a tracking value of 1000 for a 12 point font places about 4mm between each character.

A negative value tightens the letter spacing noticeably.

The text drawing action applied to each character defaults to `textoutlines(... :fill)`.

If `startnewpath` is true, each character is acted on separately. To clip and track text, specify the clip action and avoid resetting the clipping path for each character.

```julia
newpath()
texttrack(t, O + (0, 80), 200, action=:clip, startnewpath=false)
...
clipreset()
```

TODO Is it possible to fix strings with combining characters such as "̈"?
