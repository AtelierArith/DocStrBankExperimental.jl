```
Smartphore( size )
```

Create a counting semaphore that allows at most `size` acquires to be in use at any time.  The only difference with the Base Semaphore call is that Smartphores tell you which permit id you received, which can e.g. be helpful if there are `size` bits of prereserved memory to be shared.

Each acquire must be matched with a release. This provides a acquire & release memory ordering on acquire/release calls.
