```
sumsy_transfer(source::Balance,
                destination::Balance,
                sumsy::SuMSy,
                amount::Real,
                timestamp::Int = 0;
                comment = "")
```

Transfer an amount of SuMSy money from one balance sheet to another. No more than the available amount of money can be transferred. Negative amounts result in a transfer from destination to source.
