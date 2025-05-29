```
SessionStorageManagement()::Nothing
```

Manages the session storage. It's is a infinite loop that runs every 10 second. It checks if the session has expired and if it has, it removes it from the session storage. Don't need to call this function, it is called automatically by **init**() function and  runs assyncronously.

# Return

The function returns nothing.
