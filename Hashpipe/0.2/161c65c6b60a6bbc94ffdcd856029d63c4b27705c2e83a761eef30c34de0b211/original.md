```
status_chkinit(p_status::Ref{status_t})
```

Check the status buffer for appropriate formatting (existence of "END"). If not found, zero it out and add END.
