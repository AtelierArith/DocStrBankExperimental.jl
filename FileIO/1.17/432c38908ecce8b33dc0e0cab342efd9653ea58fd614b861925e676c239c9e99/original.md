```
DataFormat{sym}()
```

Indicates a known binary or text format of kind `sym`, where `sym` is always a symbol. For example, a .csv file might have `DataFormat{:CSV}()`.

An easy way to write `DataFormat{:CSV}` is `format"CSV"`.
