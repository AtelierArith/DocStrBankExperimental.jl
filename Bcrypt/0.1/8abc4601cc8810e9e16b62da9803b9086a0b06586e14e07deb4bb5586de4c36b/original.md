```
GenerateFromPassword returns the bcrypt hash of the password at the given cost.
If the cost given is less than `MinCost`, the cost will be set to `DefaultCost`, instead.
Use `CompareHashAndPassword`, as defined in this package, to compare the returned hashed password with its cleartext version.
```
