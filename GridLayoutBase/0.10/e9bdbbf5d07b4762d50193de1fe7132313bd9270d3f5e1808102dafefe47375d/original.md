```
struct Auto
```

If used as a `GridLayout`'s row / column size and `trydetermine == true`, signals to the `GridLayout` that the row / column should shrink to match the largest determinable element inside. If no size of a content element can be determined, the remaining space is split between all `Auto` rows / columns according to their `ratio`.

If used as width / height of a layoutable element and `trydetermine == true`, the element's computed width / height will report the auto width / height if it can be determined. This enables a parent `GridLayout` to adjust its column / rowsize to the element's width / height. If `trydetermine == false`, the element's computed width / height will report `nothing` even if an auto width / height can be determined, which will prohibit a parent `GridLayout` from adjusting a row / column to the element's width / height. This is useful to, e.g., prohibit a `GridLayout` from shrinking a column's width to the width of a super title, even though the title's width can be auto-determined.

The `ratio` is ignored if `Auto` is used as an element size.
