Walk along the path at a fixed sampling interval, calling the callback function at each interval

The sampling process continues until the whole path is sampled, or the callback returns a non-zero value

  * path         - the path to sample
  * step_size    - the distance along the path for subsequent samples
  * return       - tuple (error code, configuration vector). If error code != 0, then `nothing` is returned as the second argument

```

```
