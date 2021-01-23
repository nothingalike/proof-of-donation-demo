![Image of Mission Drive Pools](https://avatars.githubusercontent.com/u/77606865?s=200&v=4)
## How to Submit Proof of Donation with cardano-wallet

### 1) Download Binaries
https://github.com/input-output-hk/cardano-wallet/releases


### 2) Download Configs
https://hydra.iohk.io/build/5047936/download/1/index.html

### 3) Start cardano-node
run `./bin/cardano-node.exe run --port 6000 --database-path ./db-testnet --socket-path \\.\pipe\cardano-node-testnet --config ./configs/testnet-config.json --topology ./configs/testnet-topology.json`

### 4) Serve the cardano-wallet api
run `./bin/cardano-wallet.exe serve --testnet ./configs/testnet-byron-genesis.json --node-socket \\.\pipe\cardano-node-testnet --database ./wallets-testnet --log-level INFO`

 - While syncing, `./bin/cardano-wallet.exe network information` may look like this
```
{
    "node_tip": {
        "height": {
            "quantity": 259718,
            "unit": "block"
        },
        "time": "2019-09-23T05:00:16Z",
        "epoch_number": 12,
        "absolute_slot_number": 260760,
        "slot_number": 1560
    },
    "sync_progress": {
        "status": "syncing",
        "progress": {
            "quantity": 11.01,
            "unit": "percent"
        }
    }
}
```

### 5) Create a wallet
Docs: https://input-output-hk.github.io/cardano-wallet/api/edge/#tag/Wallets

run: `./bin/cardano-address.exe recovery-phrase generate`



### 6) Fund wallet

### 7) Create JSON File aka Proof of Donation
```
{
    "123": {
        "map": [
            {
                "k": {
                    "string": "PoolId"
                },
                "v": {
                    "string": "my-awesome-pool-id"
                }
            },
            {
                "k": {
                    "string": "Reason"
                },
                "v": {
                    "string": "LIFT Pool Charity Donation Receipt"
                }
            },
            {
                "k": {
                    "string": "Charity"
                },
                "v": {
                    "string": "No Kid Hungry"
                }
            },
            {
                "k": {
                    "string": "FundraiserUrl"
                },
                "v": {
                    "string": "http://join.nokidhungry.org/goto/liftstakepool"
                }
            },
            {
                "k": {
                    "string": "PoolTicker"
                },
                "v": {
                    "string": "LIFT"
                }
            },
            {
                "k": {
                    "string": "DonationDate"
                },
                "v": {
                    "string": "2021-02-01T12:30:00ST"
                }
            },
            {
                "k": {
                    "string": "DonationAmount"
                },
                "v": {
                    "string": "100"
                }
            },
            {
                "k": {
                    "string": "CharityFundName"
                },
                "v": {
                    "string": "Ending Childhood Hunger in America"
                }
            },
            {
                "k": {
                    "string": "EpochofDonation"
                },
                "v": {
                    "string": "245"
                }
            },
            {
                "k": {
                    "string": "DonationCurrency"
                },
                "v": {
                    "string": "USD"
                }
            },
            {
                "k": {
                    "string": "DonationFrequency"
                },
                "v": {
                    "string": "Monthly"
                }
            },
            {
                "k": {
                    "string": "PaymentMethodType"
                },
                "v": {
                    "string": "Paypal"
                }
            },
            {
                "k": {
                    "string": "PaymentMethodTransactionId"
                },
                "v": {
                    "string": "paypal-transaction-id"
                }
            },
            {
                "k": {
                    "string": "CharityReferencePaymentID"
                },
                "v": {
                    "string": "charity-transaction-id"
                }
            }
        ]
    }
}
```

### 8) Calculate Fees & Submit Transaction with Metadata
https://input-output-hk.github.io/cardano-wallet/api/edge/#tag/Transactions