```
log_text(logger::TBLogger, name::String, text::Any; step=step(logger))
```

Logs text with name `name` at step `step`

  * text: If text is a 2-D or 3-D `Array`, it will be rendered as a table or a list. Any other data will be represented as string
