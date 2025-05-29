```
is_mutts_type(t::Type) -> Bool
```

Returns true if type `t` was created via the `@mutt` macro, meaning it is a Mutable Til Shared type, and implements the *mutable-until-shared* discipline. These types start out mutable, and can be saved in a frozen version via `mark_immutable!` and `branch!`.
