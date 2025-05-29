```
gaspi_notification_num(notification_num)
```

Get the number of available notification ids. Important to note is that the allowed ids are in [ 0, notification_num ) .

### Parameters

  * `notification_num`: Output parameter with the number of available notifications ids.

### Returns

GASPI_SUCCESS in case of success, GASPI_ERROR in case of error.

### Prototype

```c
gaspi_return_t gaspi_notification_num (gaspi_number_t * const notification_num);
```
