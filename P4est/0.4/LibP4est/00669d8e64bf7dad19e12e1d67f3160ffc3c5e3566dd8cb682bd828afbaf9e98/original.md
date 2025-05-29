```
sc_package_unlock(package_id)
```

Release a pthread mutex lock. If configured without –enable-pthread, this function does nothing. This function must be follow a matching sc*package*lock.

### Parameters

  * `package_id`:[in] Either -1 for an undefined package or an id returned from sc*package*register. Depending on the value, the appropriate mutex is chosen. Thus, we may overlap locking calls with distinct package_id.

### Prototype

```c
void sc_package_unlock (int package_id);
```
