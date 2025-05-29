```
find_hashpipe_thread(name)
```

Find a Hashpipe thread with the given name.

Generally used only by the hashpipe executable.  Returns a pointer to its hashpipe*thread*desc_t structure or NULL if a test with the given name is not found.

Names are case-sensitive.
