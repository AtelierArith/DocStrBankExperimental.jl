```
add_member_weights!(setup::StaticSetup)
```

Add the weights that each ALL members exert on the setup as forces to their corresponding nodes.

  * Note that nothing is checking if this function is being called multiple times, if you accidentally call this function twice, members will just act like they're twice as heavy.
