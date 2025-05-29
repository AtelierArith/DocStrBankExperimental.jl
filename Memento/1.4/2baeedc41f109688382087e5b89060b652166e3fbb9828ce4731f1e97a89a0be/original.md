```
DefaultHanlder
```

The DefaultHandler manages any `Formatter`, `IO` and `Record`.

Fields:

  * fmt: a `Formatter` for converting `Record`s to `Strings`
  * io: an `IO` type for printing `String` to.
  * opts: a dictionary of optional arguments such as :is*colorized and :colors   Ex) ```Dict{Symbol, Any}(           :is*colorized => true,           :opts[:colors] => Dict{AbstractString, Symbol}(               "debug" => :blue,               "info" => :green,               ...           )       )```
