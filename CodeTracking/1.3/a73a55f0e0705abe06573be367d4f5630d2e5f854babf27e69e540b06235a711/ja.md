```
loc = whereis(sf::StackFrame)
```

スタックトレースの単一フレームの位置情報を返します。もし `sf` がインライン化されたフレームに対応している場合、`loc` は `nothing` になります。それ以外の場合、`loc` は `(filepath, line)` になります。
