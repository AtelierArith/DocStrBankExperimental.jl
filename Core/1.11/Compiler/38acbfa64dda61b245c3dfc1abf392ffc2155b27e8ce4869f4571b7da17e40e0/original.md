```
cnd::InterConditional
```

Similar to `Conditional`, but conveys inter-procedural constraints imposed on call arguments. This is separate from `Conditional` to catch logic errors: the lattice element name is `InterConditional` while processing a call, then `Conditional` everywhere else. Thus `InterConditional` does not appear in `CompilerTypes`—these type's usages are disjoint—though we define the lattice for `InterConditional`.
