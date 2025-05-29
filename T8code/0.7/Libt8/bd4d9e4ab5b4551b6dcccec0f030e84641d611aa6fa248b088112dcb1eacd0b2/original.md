```
t8_forest_set_scheme(forest, scheme)
```

Set the element scheme associated to a forest. By default, the forest takes ownership of the scheme such that it will be destroyed when the forest is destroyed. To keep ownership of the scheme, call t8*scheme*ref before passing it to t8*forest*set_scheme. This means that it is ILLEGAL to continue using scheme or dereferencing it UNLESS it is referenced directly before passing it into this function.

# Arguments

  * `forest`:[in,out] The forest whose scheme variable will be set.
  * `scheme`:[in] The scheme to be set. We take ownership. This can be prevented by referencing **scheme**.

### Prototype

```c
void t8_forest_set_scheme (t8_forest_t forest, t8_scheme_cxx_t *scheme);
```
