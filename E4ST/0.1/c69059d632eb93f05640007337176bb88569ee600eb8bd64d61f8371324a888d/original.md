```
modify_model!(ret::Retrofit, config, data, model)
```

Modifies the model for retrofits.  Only happens once, for all retrofits.

  * Constrains the sum of the capacities of the original generators and the retrofits is less than the original max and greater than the original min by adding constraints `cons_pcap_gen_retro_min` and `cons_pcap_gen_retro_max`
  * Removes the `cons_pcap_gen_noadd` constraints for prior to and on the retrofit year.
  * Fix the capacity of the new retrofit generators to 0 before the retrofit year.
