```
struct Keystorke
```

Structure that defines a keystroke.

# Fields

  * `value`: String representing the keystroke.
  * `ktype`: Type of the key (`:char`, `:F1`, `:up`, etc.).
  * `alt`: `true` if ALT key was pressed (only valid if `ktype != :char`).
  * `ctrl`: `true` if CTRL key was pressed (only valid if `ktype != :char`).
  * `shift`: `true` if SHIFT key was pressed (only valid if `ktype != :char`).
