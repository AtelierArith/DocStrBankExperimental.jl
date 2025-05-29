```
gaspi_print_error(error_code, error_message)
```

Translate a error code to a text message. NOTE: the parameter error_message will allocate memory which the application must de-allocate (using free())

### Parameters

  * `error_code`: The error code to translate.
  * `error_message`: Output parameter with the text message.

### Returns

GASPI_SUCCESS in case of SUCCESS, GASPI_ERR_MEMALLOC in case of error there was an error allocating the error_message buffer.

### Prototype

```c
gaspi_return_t gaspi_print_error( gaspi_return_t error_code, gaspi_string_t *error_message);
```
