```
draw_boxes(img::Array, model::YOLO.Yolo, padding::Array, results)
draw_boxes!(img::Array, model::YOLO.Yolo, padding::Array, results)
```

Draw class-colored boxes with conf labels on image for each BBOX result. With `draw_boxes!` if `img` is not a color image only boxes are drawn in black.
