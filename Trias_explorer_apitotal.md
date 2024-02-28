# api 接口说明

## api/index_base_info

链基本信息,24小时交易利率和7天交易历史信息

### 请求方式

GET

### 请求地址

/api/index_base_info

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |


### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| return_data      | dict |   返回具体数据             |

**`return_data`说明**
| 字段名 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| transactionsHistory     | dict    | 最近7天账户交易数 |
| transactionRate      | double |   最近1天内平均每小时交易数量             |
| addresses      | int |   账户地址数             |
| transactions      | int |   交易数             |
| lastBlockNumber      | int |   最新的区块号             |
| lastBlockCredit      | int |   最新区块的可信值             |
| lastBlockFees      | None |   该字段暂未使用             |
| lastTransactionFees      | int list |   最新交易费用             |
| totalDifficulty      | None |   该字段暂未使用             |
| unconfirmed      | int |   最近活跃的账号数量             |
| richList      | list |   最近活跃账户详情             |


#### tm返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| return_data      | dict |   返回具体数据             |

**`return_data`说明**
| 字段名 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| transactionsHistory     | dict    | 最近7天账户交易数 |
| transactionRate      | double |   最近1天内平均每小时交易数量             |
| addresses      | int |   账户地址数             |
| transactions      | int |   交易数             |
| lastBlockNumber      | int |   最新的区块号             |
| lastBlockCredit      | int |   最新区块的可信值             |
| lastBlockFees      | None |   该字段暂未使用             |
| lastTransactionFees      | int list |   最新交易费用             |
| totalDifficulty      | None |   该字段暂未使用             |
| unconfirmed      | int |   最近活跃的账号数量             |
| richList      | list |   最近活跃账户详情             |



### 返回数据示例
#### bsc返回数据示例
```json
{
  "code": 200,
  "return_data": {
    "transactionsHistory": {
      "04/03": 0,
      "04/02": 0,
      "04/01": 0,
      "03/31": 0,
      "03/30": 1,
      "03/29": 0,
      "03/28": 0
    },
    "transactionRate": 0.0,
    "addresses": 16,
    "transactions": 4835,
    "lastBlockNumber": 9997,
    "lastBlockCredit": 1035391,
    "lastBlockFees": "None",
    "lastTransactionFees": [24444],
    "totalDifficulty": "None",
    "unconfirmed": 16,
    "richList": [
      {
        "address": "0x0000000000000000000000000000000000001000",
        "balance": "0x1036fcc8d383aadd8c",
        "time": "2023-03-30 11:02:18"
      },
      {
        "address": "0x2f89dce87bcdb2b0312d58eaebdd153e85efce0b",
        "balance": "0x0",
        "time": "2023-03-30 11:02:18"
      },
      {
        "address": "0x947dd1558257a631049fad9d686f427f86033c16",
        "balance": "0x14dfda0cb40bd3a851cf",
        "time": "2023-03-30 11:02:18"
      },
      {
        "address": "0x0000000000000000000000000000000000001002",
        "balance": "0x114bb84dae6a4fdb4",
        "time": "2023-03-30 11:02:17"
      },
      {
        "address": "0x0000000000000000000000000000000000001009",
        "balance": "0x0",
        "time": "2023-03-30 11:02:17"
      },
      {
        "address": "0x0af48384f2a5e6af457faec584dc5593d0ad370e",
        "balance": "0x12c0e79c9a48083c5652",
        "time": "2023-03-30 11:02:17"
      },
      {
        "address": "0x29da95fa6ed88b431218a54bd8dfead68918a3b5",
        "balance": "0x33b44d06adf51d4a01",
        "time": "2023-03-30 11:02:17"
      },
      {
        "address": "0x3b6e67c4c837db054ac719892f871264e1456cdf",
        "balance": "0xbda21200",
        "time": "2023-03-30 11:02:14"
      }
    ]
  }
}
```

#### tm返回数据示例
```json
{
    "code":200,
    "return_data":{
        "transactionsHistory":{
            "04/03":0,
            "04/02":0,
            "04/01":0,
            "03/31":0,
            "03/30":0,
            "03/29":0,
            "03/28":0
        },
        "transactionRate":0,
        "addresses":16,
        "transactions":22070,
        "lastBlockNumber":43065,
        "lastBlockCredit":3662783,
        "lastBlockFees":"None",
        "lastTransactionFees":[
            null
        ],
        "totalDifficulty":"None",
        "unconfirmed":0,
        "richList":[

        ]
    }
}
```




## api/index_latest_blocks

最近20个区块详情,如果现有区块数量>=20则size为20,否则返回一个小于20区块详情列表

### 请求方式

GET

### 请求地址

api/index_latest_blocks

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |

### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| size     | int    | 最近区块数量如果现有区块数量>=20则size为20,否则返回一个小于20的数 |
| return_data      | list dict |   返回区块详情列表             |

**区块详情**

| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| number     | int    | 区块号 |
| size     | int    | 区块大小 |
| timestamp      | int |   区块时间戳             |
| hash     | string |   区块哈希值             |    
| blockReward     | 0 |   区块奖励,该字段未使用             |
| transactionsCount     | int |   交易数量             |
| credit_max     | int |   可信分             |
| time     | string |   交易时间             |

### 返回数据示例
#### bsc返回数据示例
```json
{
    "code":200,
    "size":20,
    "return_data":[
        {
            "number":9997,
            "size":767,
            "timestamp":1675387460,
            "hash":"0x3d8f1348a2d55bb89b2c3d8fb1999f7bbb465cbf69ef53702843ae48b4fee495",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1030507,
            "time":"2023-02-03 01:24:20"
        },
        {
            "number":9996,
            "size":767,
            "timestamp":1675387450,
            "hash":"0x79bf66e8e96b4f4cc97ffbbbd00dfeda074bfb8ffe3d96c6571aee8eb799b745",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1008929,
            "time":"2023-02-03 01:24:10"
        },
        {
            "number":9994,
            "size":767,
            "timestamp":1675387430,
            "hash":"0xce0730fc94f82b60bd5de975dab07dda33f50efb32aec4a00e147486bf73dfd7",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1003330,
            "time":"2023-02-03 01:23:50"
        },
        {
            "number":9993,
            "size":767,
            "timestamp":1675387420,
            "hash":"0xe8e0f48ba4f5e07f46da11f858f904c2c2514c40acfd2996bc9dd5e481b039a9",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":986934,
            "time":"2023-02-03 01:23:40"
        },
        {
            "number":9991,
            "size":767,
            "timestamp":1675387400,
            "hash":"0xec8b2c885980b15c4d0efb6f456bc9660181365fecf634c33bdc1c7690e76d33",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1030507,
            "time":"2023-02-03 01:23:20"
        },
        {
            "number":9990,
            "size":767,
            "timestamp":1675387390,
            "hash":"0x9e796ed06d20e07b177cc4304c972c7464d20e63b118883ae16ce3a311dc56e0",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1008929,
            "time":"2023-02-03 01:23:10"
        },
        {
            "number":9989,
            "size":767,
            "timestamp":1675387380,
            "hash":"0x6c7161755a04fcbf1dfc8d347d981579d34734500a2623e5630955dc60a91f10",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":86326,
            "time":"2023-02-03 01:23:00"
        },
        {
            "number":9987,
            "size":767,
            "timestamp":1675387360,
            "hash":"0x2d1c6c5d7c01cd3e6ddde7f12450b6af4c3036b976b59f8437b8dfab92cc88ba",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":986934,
            "time":"2023-02-03 01:22:40"
        },
        {
            "number":9985,
            "size":767,
            "timestamp":1675387340,
            "hash":"0x1b5be3771fae0f016da2dc6103675030c79433f2dca7c4747e600af8900162fa",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1030507,
            "time":"2023-02-03 01:22:20"
        },
        {
            "number":9984,
            "size":767,
            "timestamp":1675387330,
            "hash":"0xef75bee405d8cdcb3ee5751b856350a3cdf6390d412b518942c4e14a9ae9a4fc",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1008929,
            "time":"2023-02-03 01:22:10"
        },
        {
            "number":9983,
            "size":767,
            "timestamp":1675387320,
            "hash":"0x5fe8fa174586a20ab10fdb424772fd9c7520515e647afb5a2f72597cd9d4617e",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":86326,
            "time":"2023-02-03 01:22:00"
        },
        {
            "number":9982,
            "size":767,
            "timestamp":1675387310,
            "hash":"0x0030b4c94ebbd237684e0b7f66b3eb8e0553f392a7ee99d9db55ea2db034c373",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1003330,
            "time":"2023-02-03 01:21:50"
        },
        {
            "number":9981,
            "size":767,
            "timestamp":1675387300,
            "hash":"0x514dd313192ffc8474b3345082ac349cd492851dc1441272578c080115502b34",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":986934,
            "time":"2023-02-03 01:21:40"
        },
        {
            "number":9980,
            "size":767,
            "timestamp":1675387290,
            "hash":"0x77385401a7fdd16d21df548f978420477d9115b8ef4d2b1ece562234def07608",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1035391,
            "time":"2023-02-03 01:21:30"
        },
        {
            "number":9978,
            "size":767,
            "timestamp":1675387270,
            "hash":"0x4fc4380f112422a828becade2ac330f92574c24eceebb55bb9af702e5785825a",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1008929,
            "time":"2023-02-03 01:21:10"
        },
        {
            "number":9975,
            "size":767,
            "timestamp":1675387240,
            "hash":"0x1b75b266f6808fae8d7acffb9c97c9ad1f0e582ab90c63119e83ad86e41ae63c",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":986934,
            "time":"2023-02-03 01:20:40"
        },
        {
            "number":9973,
            "size":767,
            "timestamp":1675387220,
            "hash":"0x9c36976f27b6d314d5a3e868f5099db431a45c5e220f66fdf3d8cdfcb2254a3b",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1030507,
            "time":"2023-02-03 01:20:20"
        },
        {
            "number":9972,
            "size":767,
            "timestamp":1675387210,
            "hash":"0xaf09dc868a9b0300bc3cfe118df1566d5dbca2714ca979b8c884c40cc9a1dc09",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1008929,
            "time":"2023-02-03 01:20:10"
        },
        {
            "number":9970,
            "size":767,
            "timestamp":1675387190,
            "hash":"0x522fd16ede920e83fb13e957304025c0bdae6fde32014386bf12d1ced6d306cd",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":1003330,
            "time":"2023-02-03 01:19:50"
        },
        {
            "number":9969,
            "size":767,
            "timestamp":1675387180,
            "hash":"0x59e80adea886910f4d0b86a83d0f5647aadfa89a40e31af34a8b57d5bb2ce359",
            "blockReward":0,
            "transactionsCount":0,
            "credit_max":986934,
            "time":"2023-02-03 01:19:40"
        }
    ]
}
```

#### tm返回数据示例
```json
{
    "code":200,
    "size":20,
    "return_data":[
        {
            "number":43065,
            "size":92,
            "timestamp":1678939378,
            "hash":"C44A392AB59F8B878BD4B40BCD8D8B2722198B8A7F481A16F0A192ACEFBE3790",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662783,
            "time":"2023-03-16 04:02:58"
        },
        {
            "number":43064,
            "size":92,
            "timestamp":1678939372,
            "hash":"64CB58BC1C30D6C559A0665355224A0584444113F46DB52416E1EB1BCB50F94A",
            "blockReward":null,
            "transactionsCount":2,
            "credit_max":3662783,
            "time":"2023-03-16 04:02:52"
        },
        {
            "number":43063,
            "size":92,
            "timestamp":1678939366,
            "hash":"F5B5522D2D4C0D6621518187582BB03772F9E6CC759DD70A66D1B1C34FAFC820",
            "blockReward":null,
            "transactionsCount":2,
            "credit_max":3662780,
            "time":"2023-03-16 04:02:46"
        },
        {
            "number":43062,
            "size":92,
            "timestamp":1678939364,
            "hash":"AE798BAD4B1C5B886FED0DFF45EFA880EBC9D429854BE7403E7B26161F504E14",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662772,
            "time":"2023-03-16 04:02:44"
        },
        {
            "number":43061,
            "size":92,
            "timestamp":1678939356,
            "hash":"B50487980BE8339DD7023F5C4FBAAF32421DBD3A27EF789698B399BB124DEBD1",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662772,
            "time":"2023-03-16 04:02:36"
        },
        {
            "number":43060,
            "size":92,
            "timestamp":1678939347,
            "hash":"CAE8061A687D4DBA19D646FDE06F760582454A49A89132EA727FAB55CD67307C",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662764,
            "time":"2023-03-16 04:02:27"
        },
        {
            "number":43059,
            "size":92,
            "timestamp":1678939345,
            "hash":"2925779D5F9DD5D7AABDAF3F0A69BC01BA1688ACEEF178CBC50F5F7448138FA5",
            "blockReward":null,
            "transactionsCount":0,
            "credit_max":3662756,
            "time":"2023-03-16 04:02:25"
        },
        {
            "number":43058,
            "size":92,
            "timestamp":1678939333,
            "hash":"B4D6BBEF333233C224083F7DDD5673DF73746D189AE9BE50C98D6D73C2798351",
            "blockReward":null,
            "transactionsCount":3,
            "credit_max":3662756,
            "time":"2023-03-16 04:02:13"
        },
        {
            "number":43057,
            "size":92,
            "timestamp":1678939332,
            "hash":"F0D11FEF08E99F8C1CA06924F78F483D726B1936C8D43DDA5BCD93433FFAD58D",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662748,
            "time":"2023-03-16 04:02:12"
        },
        {
            "number":43056,
            "size":92,
            "timestamp":1678939330,
            "hash":"9E184706D30DBFDA71DF8A9D2126693FCE5166640D73B1B734C66F56A0545D3D",
            "blockReward":null,
            "transactionsCount":0,
            "credit_max":3662749,
            "time":"2023-03-16 04:02:10"
        },
        {
            "number":43055,
            "size":92,
            "timestamp":1678939327,
            "hash":"C8554193B995AA253979B67D78AA612DEB6EBC22D36CDFDF514E645EBEF129B3",
            "blockReward":null,
            "transactionsCount":2,
            "credit_max":3662743,
            "time":"2023-03-16 04:02:07"
        },
        {
            "number":43054,
            "size":92,
            "timestamp":1678939322,
            "hash":"801E9BF037EA09DAE86FD9BAB5D7C4BE3D8989ACAE239CCFF005CC5A5CC43D37",
            "blockReward":null,
            "transactionsCount":2,
            "credit_max":3662743,
            "time":"2023-03-16 04:02:02"
        },
        {
            "number":43053,
            "size":92,
            "timestamp":1678939318,
            "hash":"4A54A172947C073496A1C9C1E9CB01815712C2B7EA38CEFEE4A8908CED66A00C",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662736,
            "time":"2023-03-16 04:01:58"
        },
        {
            "number":43052,
            "size":92,
            "timestamp":1678939316,
            "hash":"4D88012322926F2E540BA587A49BB44FE17A791A479DE83205F467C2E20B2D0F",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662734,
            "time":"2023-03-16 04:01:56"
        },
        {
            "number":43051,
            "size":92,
            "timestamp":1678939309,
            "hash":"03E1C8A4A46223317D2B2EBCB95A5520FC5041B634E74E2C3576CFDCF93B004F",
            "blockReward":null,
            "transactionsCount":3,
            "credit_max":3662733,
            "time":"2023-03-16 04:01:49"
        },
        {
            "number":43050,
            "size":92,
            "timestamp":1678939307,
            "hash":"C30DEDCA8FBA177CD6D0D90722EEC64A783F873296817087972503505284133B",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662729,
            "time":"2023-03-16 04:01:47"
        },
        {
            "number":43049,
            "size":92,
            "timestamp":1678939302,
            "hash":"64AF8D9E5513F6052D63123F3B3493DCC5ACBF61B7D9E4B0C3B83698C35DEC6E",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662729,
            "time":"2023-03-16 04:01:42"
        },
        {
            "number":43048,
            "size":92,
            "timestamp":1678939298,
            "hash":"7FAD822E7B1387915DE108B0674CFF35AE8AA6AFD2910AB820E989B2793E5927",
            "blockReward":null,
            "transactionsCount":3,
            "credit_max":3662721,
            "time":"2023-03-16 04:01:38"
        },
        {
            "number":43047,
            "size":92,
            "timestamp":1678939293,
            "hash":"5842ACCA47216935FAB73763DA6946134D6CFD868C4EF5F803A3DE84825A38EE",
            "blockReward":null,
            "transactionsCount":0,
            "credit_max":3662714,
            "time":"2023-03-16 04:01:33"
        },
        {
            "number":43046,
            "size":92,
            "timestamp":1678939292,
            "hash":"93F9CE0321CACD051A7826110ECAB82F35B0F395C20D9D731FA3B9A08DA00E7A",
            "blockReward":null,
            "transactionsCount":1,
            "credit_max":3662717,
            "time":"2023-03-16 04:01:32"
        }
    ]
}
```



## api/index_recent_transactions

最近20个交易详情,如果现有交易数量>=20则size为20,否则返回一个小于20区块详情列表

### 请求方式

GET

### 请求地址

/api/index_recent_transactions

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |


### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| size     | int    | 最近交易数量,如果现有交易数量>=20则size为20,否则返回一个小于20的数 |
| return_data      | list dict |   返回交易详情列表             |

**交易详情**

| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| source     | string    | 交易from地址 |
| to     | string    | 交易to地址 |
| hash     | string |   交易哈希值             |
| blockNumber     | int    | 交易所属区块的区块号 |
| timestamp      | int |   区块时间戳             |
| txstr     | string |   交易input             |
| type     | int |   交易类型,暂未用到             |
| time     | string |   交易时间             |




#### tm返回数据
tm无此接口

### 返回数据示例
#### bsc返回数据示例
```json
{
    "code":200,
    "size":20,
    "return_data":[
        {
            "source":"0x872c815e5d50d2cb497aca781e95af0da3616991",
            "to":"0xb42cb187d7738fa9c14db86e0a25014d6c296bcd",
            "hash":"0x5500f6755c43cdfe7f8a04347974486deb60845bd871a5727f07b41f1934690c",
            "blockNumber":351273,
            "timestamp":1680230424,
            "tx_str":"0x",
            "type":0,
            "time":"2023-03-31 02:40:24"
        },
        {
            "source":"0x38580efe497b22acc29783273e725a2a4f2aeea4",
            "to":"0x0000000000000000000000000000000000001001",
            "hash":"0xa2273891a95472a205dd4ce57c26abc34cef5807eba1d13229e4162ddc2d6f08",
            "blockNumber":3948,
            "timestamp":1675326932,
            "tx_str":"0xc96be4cb0000000000000000000000000000000000000000000000000000000000000000",
            "type":0,
            "time":"2023-02-02 08:35:32"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001001",
            "hash":"0x64427d3787510b8555bf3b216cc3b17870f4ff926fb5224b0f3396d6cce9e208",
            "blockNumber":3942,
            "timestamp":1675326861,
            "tx_str":"0xc96be4cb0000000000000000000000000000000000000000000000000000000000000000",
            "type":0,
            "time":"2023-02-02 08:34:21"
        },
        {
            "source":"0x3b6e67c4c837db054ac719892f871264e1456cdf",
            "to":"0x0000000000000000000000000000000000001001",
            "hash":"0xcac821975f4a89b0e5b8b441e044619667de56d3ed0e8818e63b8acd916ede6a",
            "blockNumber":3936,
            "timestamp":1675326799,
            "tx_str":"0xc96be4cb0000000000000000000000000000000000000000000000000000000000000000",
            "type":0,
            "time":"2023-02-02 08:33:19"
        },
        {
            "source":"0x38580efe497b22acc29783273e725a2a4f2aeea4",
            "to":"0x0000000000000000000000000000000000001001",
            "hash":"0xd9d4c8a93aa8778acb3f037001de4f7c9696fb56d90ae0f5c88977750bb36a00",
            "blockNumber":3930,
            "timestamp":1675326726,
            "tx_str":"0xc96be4cb0000000000000000000000000000000000000000000000000000000000000000",
            "type":0,
            "time":"2023-02-02 08:32:06"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001001",
            "hash":"0xb474113ac10eb86105d9558f713026d601520db2dd7d135a646ecc4efef8cbf8",
            "blockNumber":3924,
            "timestamp":1675326654,
            "tx_str":"0xc96be4cb0000000000000000000000000000000000000000000000000000000000000000",
            "type":0,
            "time":"2023-02-02 08:30:54"
        },
        {
            "source":"0x38580efe497b22acc29783273e725a2a4f2aeea4",
            "to":"0x0000000000000000000000000000000000001002",
            "hash":"0x8c63d0db3f2d42d660ebdc88ea8a336589daf14741e577c164d86698f90d8ad7",
            "blockNumber":3920,
            "timestamp":1675326607,
            "tx_str":"0x",
            "type":0,
            "time":"2023-02-02 08:30:07"
        },
        {
            "source":"0x947dd1558257a631049fad9d686f427f86033c16",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0xfcd3b130711b99d39d5c1565f39d257158ffe4a231a4090eab140c759da584ea",
            "blockNumber":3920,
            "timestamp":1675326607,
            "tx_str":"0xed996f1f0000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000060000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16000000000000000000000000aca316109004339bf17df2e237c66cfee5c7c429",
            "type":0,
            "time":"2023-02-02 08:30:07"
        },
        {
            "source":"0x38580efe497b22acc29783273e725a2a4f2aeea4",
            "to":"0x0000000000000000000000000000000000001000",
            "hash":"0x1903d50410b350050614aa56e531cf906473d50dba987d7726ae9b24c9be310a",
            "blockNumber":3920,
            "timestamp":1675326607,
            "tx_str":"0xf340fa0100000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea4",
            "type":0,
            "time":"2023-02-02 08:30:07"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0xe79ac4b9afbf6d29154805d318a3bd5570d781dbb88ddf61deb4e0350e24a334",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f0000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000050000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x947dd1558257a631049fad9d686f427f86033c16",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0x4f2e2b341e8549a90a3b1cdbc22d775191eb70317b5a1b7980b62cc91abf5f4a",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f00000000000000000000000000000000000000000000000000000000000000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0x1e026b168c3e4a3e5b95f64bedf4fd3fc4c5267f595bcc229a4bea2cb490c75c",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f0000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000050000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0x11768d9087bdc36642eae2053c22dcfc680e676000dab7e43c10b5911052d97e",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f0000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000050000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0x84c8cf3bd80ca1cc6bc0b19d11a7dcfe24cb8d306a81c098aa63407cd5156b9f",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f0000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000050000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0xf3cab0937b22840bcea8eda399ab247db27a3060259b8f8f91671accf8f65b18",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f00000000000000000000000000000000000000000000000000000000000000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0xb2c357e9f71ae3483ba98dbcfc3f27d03526859992b13cecc4210808d7f62e17",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f00000000000000000000000000000000000000000000000000000000000000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0x5d32c5d8abbe55a4a52df8ee7a36033e9d5b49dc6c4492e20689656e39545802",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f00000000000000000000000000000000000000000000000000000000000000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0x424c8c149442770ced35bf0fe76b71ad4371db38697831ab60634af83d054954",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f0000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000050000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0x78bde20b8c1db6a44af4433960038b2902aa9ab67bdbe289c7e5fcf6956c7885",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f0000000000000000000000000000000000000000000000000000000000000040000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000050000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        },
        {
            "source":"0x0af48384f2a5e6af457faec584dc5593d0ad370e",
            "to":"0x0000000000000000000000000000000000001009",
            "hash":"0x17323c6ef1edc39cbcc539c6a734d7eeb864eb577bb885d9d96b0667d1c824f7",
            "blockNumber":3918,
            "timestamp":1675326584,
            "tx_str":"0xed996f1f00000000000000000000000000000000000000000000000000000000000000400000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000600000000000000000000000000000000000000000000000000000000000000000000000000000000000000000af48384f2a5e6af457faec584dc5593d0ad370e00000000000000000000000029da95fa6ed88b431218a54bd8dfead68918a3b500000000000000000000000038580efe497b22acc29783273e725a2a4f2aeea40000000000000000000000003b6e67c4c837db054ac719892f871264e1456cdf000000000000000000000000947dd1558257a631049fad9d686f427f86033c16",
            "type":0,
            "time":"2023-02-02 08:29:44"
        }
    ]
}
```

#### tm返回数据示例

```json
{
    "code":200,
    "size":2,
    "return_data":[
        {
            "source":null,
            "to":null,
            "hash":"ea2c7f1dbad4cec1763367f361722617f0b46ab7e2b44703c8ebc69b68eea20d",
            "blockNumber":43065,
            "timestamp":1678939378,
            "tx_str":"CCaadCCs11RKVcc",
            "type":1,
            "time":"2023-03-16 04:02:58"
        },
        {
            "source":null,
            "to":null,
            "hash":"25c7f3d5fd10a7774ef35b0386906256ddaf086136b9f4f6b0f1aa0a0a83b2b1",
            "blockNumber":43064,
            "timestamp":1678939372,
            "tx_str":"CCaadCCs115muz3",
            "type":1,
            "time":"2023-03-16 04:02:52"
        }
    ]
}
```


## api/search/

搜索接口,根据关键字返回区块/账户地址/交易哈希的搜索结果,前端可根据搜索结果跳转到具体信息的详情页面

区块/账户地址/交易哈希只会返回其中之一(因为其key唯一)


### 请求方式

GET

### 请求地址

/api/search/

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |
| key        | 搜索关键字|string | 无      | 是  |

### 返回数据说明
#### bsc返回数据
- 成功返回说明
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| data_type     | block/address/transaction    | 搜索结果的数据类型 |
| block/address/transaction     | string    | 区块号/账户地址/交易哈希 |

- 失败返回示例

`{"code": 201, "message": "Error key"}`


#### tm返回数据

| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| data_type     | block/address/transaction    | 搜索结果的数据类型 |
| block/address/transaction     | string    | 区块号/账户地址/交易哈希 |

### 返回数据示例
#### bsc返回数据示例
- 搜索区块返回数据
```json
{
    "code": 200,
    "data_type": "block",
    "block_hash": "0x3d8f1348a2d55bb89b2c3d8fb1999f7bbb465cbf69ef53702843ae48b4fee495"
}
```
- 搜索账号返回数据
```json
{
    "code": 200,
    "data_type": "address",
    "address": "0x0000000000000000000000000000000000001000"
}
```

- 搜索交易返回数据
```json
{
    "code":200,
    "data_type":"transaction",
    "tx_hash":"0x5500f6755c43cdfe7f8a04347974486deb60845bd871a5727f07b41f1934690c"
}
```


#### tm返回数据示例




## api/all_blocks

区块列表


### 请求方式

GET

### 请求地址

/api/all_blocks

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |
| size        |请求每页数据大小|int | 50      | 否  |
| page        |请求页码|int | 1      | 否  |

### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| total_size     | int    | 区块大小之和 |
| page     | int    | 页码 |
|total_page | int | 总页数 |
| return_data | list dict| 区块数据列表|


**区块数据**
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| number     | int    | 区块号 |
| size     | int    | 区块大小 |
| timestamp      | int |   区块时间戳             |
| hash     | string |   区块哈希值             |    
| blockReward     | 0 |   区块奖励,该字段未使用             |
| transactionsCount     | int |   交易数量             |
| credit_max     | int |   可信分             |
| time     | string |   交易时间             |
| avgFee     | double |   交易平均花费(当前为定值:0.00332)             |


#### tm返回数据

| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| total_size     | int    | 区块大小之和 |
| page     | int    | 页码 |
|total_page | int | 总页数 |
| return_data | list dict| 区块数据列表|

return_data：同上bsc返回数据

### 返回数据示例
#### bsc返回数据示例
```json
{
    "code":200,
    "total_size":9333,
    "page":1,
    "total_page":934,
    "return_data": [
        {
            "hash":"0x3d8f1348a2d55bb89b2c3d8fb1999f7bbb465cbf69ef53702843ae48b4fee495",
            "number":9997,
            "transactionsCount":0,
            "size":767,
            "blockReward":0,
            "timestamp":1675387460,
            "credit_max":1030507,
            "time":"2023-02-03 01:24:20",
            "avgFee":0.00332
        },
        {
            "hash":"0x79bf66e8e96b4f4cc97ffbbbd00dfeda074bfb8ffe3d96c6571aee8eb799b745",
            "number":9996,
            "transactionsCount":0,
            "size":767,
            "blockReward":0,
            "timestamp":1675387450,
            "credit_max":1008929,
            "time":"2023-02-03 01:24:10",
            "avgFee":0.00332
        }      
    ]
}
```


#### tm返回数据示例
http://192.168.1.98:8620/api/all_blocks/?size=10&page=1&chain=tm

```json
{
    "code":200,
    "total_size":43065,
    "page":1,
    "total_page":4307,
    "return_data":[
        {
            "hash":"C44A392AB59F8B878BD4B40BCD8D8B2722198B8A7F481A16F0A192ACEFBE3790",
            "number":43065,
            "transactionsCount":1,
            "size":92,
            "blockReward":null,
            "timestamp":1678939378,
            "credit_max":3662783,
            "time":"2023-03-16 04:02:58",
            "avgFee":0.00332
        },
        {
            "hash":"9E184706D30DBFDA71DF8A9D2126693FCE5166640D73B1B734C66F56A0545D3D",
            "number":43056,
            "transactionsCount":0,
            "size":92,
            "blockReward":null,
            "timestamp":1678939330,
            "credit_max":3662749,
            "time":"2023-03-16 04:02:10",
            "avgFee":0.00332
        }
    ]
}
```

## api/block_info
区块详情


### 请求方式

GET

### 请求地址

/api/block_info

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |
| block_hash        |区块哈希|string | 无      | 是  |

### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| return_data | dict| 区块详情|


**区块详情**
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| number     | int    | 区块号 |
| size     | int    | 区块大小 |
| timestamp      | int |   区块时间戳             |
| difficulty      | string |   区块diffcultly值,hexstring             |
| nonce      | string |   区块nonce值|
| parentHash     | string |   上个区块哈希             |    
| nextHash     | string |   下个区块哈希             |
| miner     | string |   区块所有者             |
| gasLimit      | int |   区块gasLimit值             |
| gasUsed      | int |   区块gasUsed值             |
| credit_value | list dict |   区块可信分值             |
| total_fee      | int |   区块交易费用之和             |
| is_computed | bool| 是否计算total_fee |
|tm_height | int |   tm区块高度             |
| blockReward     | 0 |   区块奖励,该字段未使用             |
| transactionsCount     | int |   交易数量             |
| time     | string |   交易时间             |
| confirmations | int | 最新出块确认,>0为否=0时为最新  |



#### tm返回数据

| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| return_data | dict| 区块详情|

**区块详情**
同上bsc返回结构，无下面数据域
tm_height


### 返回数据示例
#### bsc返回数据示例
```json
{
    "code":200,
    "return_data":{
        "number":9997,
        "transactionsCount":0,
        "timestamp":1675387460,
        "size":767,
        "difficulty":"0x2",
        "nonce":"0x0000000000000000",
        "parentHash":"0x79bf66e8e96b4f4cc97ffbbbd00dfeda074bfb8ffe3d96c6571aee8eb799b745",
        "miner":"0x29da95fa6ed88b431218a54bd8dfead68918a3b5",
        "gasLimit":40000000,
        "credit_value":[
            {
                "0af48384f2a5e6af457faec584dc5593d0ad370e":1008970
            },
            {
                "29da95fa6ed88b431218a54bd8dfead68918a3b5":1030507
            },
            {
                "38580efe497b22acc29783273e725a2a4f2aeea4":1035391
            },
            {
                "3b6e67c4c837db054ac719892f871264e1456cdf":986934
            },
            {
                "947dd1558257a631049fad9d686f427f86033c16":1003330
            },
            {
                "aca316109004339bf17df2e237c66cfee5c7c429":86326
            }
        ],
        "is_computed":true,
        "total_fee":0,
        "gasUsed":0,
        "blockReward":0,
        "tm_height":0,
        "time":"2023-02-03 01:24:20",
        "confirmations":0,
        "nextHash":"N/A"
    }
}
```


#### tm返回数据示例

http://192.168.1.98:8620/api/block_info/?block_hash=C44A392AB59F8B878BD4B40BCD8D8B2722198B8A7F481A16F0A192ACEFBE3790&chain=tm

```json
{
    "code":200,
    "return_data":{
        "number":43065,
        "transactionsCount":1,
        "timestamp":1678939378,
        "size":92,
        "difficulty":null,
        "nonce":null,
        "parentHash":"64CB58BC1C30D6C559A0665355224A0584444113F46DB52416E1EB1BCB50F94A",
        "miner":null,
        "gasLimit":null,
        "credit_value":[
            {
                "818A6204FEC3C6F7D6A3033BA0D717C3284BABEB5D192FB5ECEACC4C51A5406F":3662783
            },
            {
                "8DC47B953386EEFDFCC3382EFE2BFD1DCC9394108C642FFEB6A43E25F5119609":3613522
            },
            {
                "AB0F612D1CE5F31E115DF81FBF63018161319E8C4857AC87A57DF7E3DC0D4B20":3662619
            },
            {
                "C100C31BE54564DF40294D54CF6313A0A381B4609C5AE1EDBE6F212E451728B6":3602319
            },
            {
                "CDD9665927C2D487F0FB4134EA3A14C0549E8433F5E7EE51A1939911907242B7":3601940
            }
        ],
        "is_computed":true,
        "total_fee":null,
        "gasUsed":null,
        "blockReward":null,
        "time":"2023-03-16 04:02:58",
        "confirmations":0,
        "nextHash":"N/A"
    }
}
```


## api/block_transactions/
区块详情


### 请求方式

GET

### 请求地址

/api/block_transactions/

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |
| block_hash        |区块哈希|string | 无      | 是  |
| size        |请求每页数据大小|int | 50      | 否  |
| page        |请求页码|int | 1      | 否  |

### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| total_size     | int    | 区块大小之和 |
| page     | int    | 页码 |
| total_page | int | 总页数 |
| return_data | list dict| 区块交易列表|


**区块交易**
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| id     | int    | 数据库主键(业务场景无用) |
| blockHash     | string    | 交易所在区块哈希 |
| source      | string |   交易from地址             |
| to      | string |   交易to地址               |
| gas      | int |   交易花费gas |
| gasPrice     | int |   交易gas价格             |    
| nonce     | int |   交易nonce值             |
| hash | string | 交易哈希 |
| transactionIndex | int |交易在区块中的index |
| value | int | 交易value值 |
| v | int | 交易签名v字段值 |
| r | string |交易签名r字段值 |
| s | string |交易签名s字段值 |
|timestamp | int | 交易时间戳|
|tx_str | string | 交易input字段 |
|type | int |交易类型|
|fee| int| 交易花费|



#### tm返回数据
同上bsc

### 返回数据示例
#### bsc返回数据示例
```json

{
    "code":200,
    "total_size":4,
    "page":1,
    "total_page":1,
    "return_data":[
        {
            "id":469385,
            "blockHash":"0x9343d87ea415f47f4176edc8d7427398fe7bf319b5d40a2f83bce35191fcf115",
            "blockNumber":344272,
            "source":"0x38580eFe497b22ACc29783273e725a2a4F2AEEA4",
            "to":"0x0000000000000000000000000000000000001000",
            "gas":9223372036854775807,
            "gasPrice":0,
            "nonce":59940,
            "hash":"0x592d7a0f22e686c072f5bb076688d25a8f29cf9704393b95a5fbcccdbe46a948",
            "transactionIndex":3,
            "value":"39375000000000",
            "v":1640061,
            "r":"0x1c9c542b2524c2e7f5f6da083224b5c2a4c8398d8b435b3e40c70dff9013f2ac",
            "s":"0x6c95194fb57b96e39731677e5ebfa0ba29756096a3a958dc3fc274895b499ece",
            "timestamp":1679042931,
            "tx_str":null,
            "type":0,
            "fee":0
        }
    ]
}
```
#### tm返回数据示例

http://192.168.1.98:8620/api/block_transactions/?block_hash=64CB58BC1C30D6C559A0665355224A0584444113F46DB52416E1EB1BCB50F94A&size=10&page=1&chain=tm

```json
{
    "code":200,
    "total_size":2,
    "page":1,
    "total_page":1,
    "return_data":[
        {
            "id":445151,
            "blockHash":"64CB58BC1C30D6C559A0665355224A0584444113F46DB52416E1EB1BCB50F94A",
            "blockNumber":43064,
            "source":null,
            "to":null,
            "gas":null,
            "gasPrice":null,
            "nonce":null,
            "hash":"c2c8e6bf889427a4d1c78408b29c04abd8333aff5df63ccc25ef9b3d83693b60",
            "transactionIndex":null,
            "value":null,
            "v":null,
            "r":null,
            "s":null,
            "gasUsed":null,
            "timestamp":1678939372,
            "tx_str":"CCaadCCs11zhY9P",
            "type":1,
            "fee":null
        },
        {
            "id":445149,
            "blockHash":"64CB58BC1C30D6C559A0665355224A0584444113F46DB52416E1EB1BCB50F94A",
            "blockNumber":43064,
            "source":null,
            "to":null,
            "gas":null,
            "gasPrice":null,
            "nonce":null,
            "hash":"25c7f3d5fd10a7774ef35b0386906256ddaf086136b9f4f6b0f1aa0a0a83b2b1",
            "transactionIndex":null,
            "value":null,
            "v":null,
            "r":null,
            "s":null,
            "gasUsed":null,
            "timestamp":1678939372,
            "tx_str":"CCaadCCs115muz3",
            "type":1,
            "fee":null
        }
    ]
}

```



## api/all_transactions/
区块详情


### 请求方式

GET

### 请求地址

/api/all_transactions/

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |
| size        |请求每页数据大小|int | 50      | 否  |
| page        |请求页码|int | 1      | 否  |

### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| total_size     | int    | 区块大小之和 |
| page     | int    | 页码 |
| total_page | int | 总页数 |
| return_data | list dict| 区块交易列表|


**区块交易**
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| blockHash     | string    | 交易所在区块哈希 |
| blockNumber    | int    | 交易所在区块号 |
| source      | string |   交易from地址             |
| to      | string |   交易to地址               |
| hash | string | 交易哈希 |
| value | string | 交易value值 |
|time | string | 交易时间|
|tx_str | string | 交易input字段 |
|type | int |交易类型|




#### tm返回数据
同上bsc

### 返回数据示例
#### bsc返回数据示例
```json

{
    "code":200,
    "total_size":4834,
    "page":1,
    "total_page":484,
    "return_data": {
        {
            "hash":"0xa2273891a95472a205dd4ce57c26abc34cef5807eba1d13229e4162ddc2d6f08",
            "source":"0x38580efe497b22acc29783273e725a2a4f2aeea4",
            "to":"0x0000000000000000000000000000000000001001",
            "value":"0x0",
            "blockNumber":3948,
            "blockHash":"0xe20b6c9b229997b9b4f79ca7d25815ff7ab557930547b1e7843d4a2e747e2402",
            "tx_str":"0xc96be4cb0000000000000000000000000000000000000000000000000000000000000000",
            "type":0,
            "time":"2023-02-02 08:35:32"
        }        
    }
}
```
#### tm返回数据示例
同上bsc



## api/transaction_info/
交易详情


### 请求方式

GET

### 请求地址

/api/transaction_info/

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |
|  txhash   | 交易哈希 | string      | 无  |  是  |


### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| return_data | dict| 交易详情 |


**交易详情**
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| id     | int    | 数据库主键(业务场景无用) |
| blockHash     | string    | 交易所在区块哈希 |
| source      | string |   交易from地址             |
| to      | string |   交易to地址               |
| gas      | int |   交易花费gas |
| gasPrice     | int |   交易gas价格             |    
| nonce     | int |   交易nonce值             |
| hash | string | 交易哈希 |
| transactionIndex | int |交易在区块中的index |
| value | int | 交易value值 |
| v | int | 交易签名v字段值 |
| r | string |交易签名r字段值 |
| s | string |交易签名s字段值 |
|timestamp | int | 交易时间戳|
|tx_str | string | 交易input字段 |
|type | int |交易类型|
|fee| int| 交易花费|
|gasLimit | int | 交易gas限制 |
|time| string| 交易时间|




#### tm返回数据
同上bsc返回

### 返回数据示例
#### bsc返回数据示例
```json
{
    "code":200,
    "return_data":{
        "id":4521,
        "blockHash":"0xe20b6c9b229997b9b4f79ca7d25815ff7ab557930547b1e7843d4a2e747e2402",
        "blockNumber":3948,
        "source":"0x38580efe497b22acc29783273e725a2a4f2aeea4",
        "to":"0x0000000000000000000000000000000000001001",
        "gas":9223372036854775807,
        "gasPrice":0,
        "nonce":559,
        "hash":"0xa2273891a95472a205dd4ce57c26abc34cef5807eba1d13229e4162ddc2d6f08",
        "transactionIndex":0,
        "value":"0x0",
        "v":"0x19067d",
        "r":"0x659b5bb024d517ef94497dc1150dfaa35ca3f934ceb4a1de951644b1319f74e6",
        "s":"0x136219a513d02938aae2a549207373a438e427770429f14425e2f7b84324e272",
        "timestamp":1675326932,
        "tx_str":"0xc96be4cb0000000000000000000000000000000000000000000000000000000000000000",
        "type":0,
        "fee":"0x0",
        "gasLimit":40000000,
        "time":"2023-02-02 08:35:32"
    }
}
```
#### tm返回数据示例

http://192.168.1.98:8620/api/transaction_info/?tx_hash=c2c8e6bf889427a4d1c78408b29c04abd8333aff5df63ccc25ef9b3d83693b60&chain=tm

```json
{
    "code":200,
    "return_data":{
        "id":445151,
        "blockHash":"64CB58BC1C30D6C559A0665355224A0584444113F46DB52416E1EB1BCB50F94A",
        "blockNumber":43064,
        "source":null,
        "to":null,
        "gas":null,
        "gasPrice":null,
        "nonce":null,
        "hash":"c2c8e6bf889427a4d1c78408b29c04abd8333aff5df63ccc25ef9b3d83693b60",
        "transactionIndex":null,
        "value":null,
        "v":null,
        "r":null,
        "s":null,
        "gasUsed":null,
        "timestamp":1678939372,
        "tx_str":"CCaadCCs11zhY9P",
        "type":1,
        "fee":null,
        "gasLimit":null,
        "time":"2023-03-16 04:02:52"
    }
}

```

## api/address/
账户详情


### 请求方式

GET

### 请求地址

/api/address/

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |
|  address   | 账户地址 | string      | 无|是  |


### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| return_data | dict| 交易详情 |


**交易详情**
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| id     | int    | 数据库主键(业务场景无用) |
| address     | string    | 账户地址 |
| balance     | string    | 账户余额 |
| address     | string    | 交易所在区块哈希 |
|time| string| 交易时间|
| txCount     | int    | 账户交易数量 |
| sent     | int    | 账户消耗value总量 |
| received     | int    | 账户接受value重量 |




#### tm返回数据
tm无address的接口请求

### 返回数据示例
#### bsc返回数据示例
```json
{
    "code":200,
    "return_data":{
        "id":8,
        "address":"0x38580efe497b22acc29783273e725a2a4f2aeea4",
        "balance":"0x32cc630acfaf06fff6",
        "time":"2023-03-30 11:02:14",
        "txCount":560,
        "sent":50000000042993645344552960,
        "received":0
    }
}
```
#### tm返回数据示例
无



## api/address_transactions/


账户详情


### 请求方式

GET

### 请求地址

/api/address_transactions/

### 请求参数

| 参数名称      | 说明      | 类型   | 默认值 | 必  |
| :----------- |:----------- |:----- | :----- | :-- |
| chain        | 链类型(default/tm)|string | default      | 否  |
| size        |请求每页数据大小|int | 10      | 否  |
| page        |请求页码|int | 1      | 否  |



### 返回数据说明
#### bsc返回数据
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| code     | int    | 状态码，200 表示成功 |
| total_size     | int    | 区块大小之和 |
| page     | int    | 页码 |
| total_page | int | 总页数 |
| return_data | list dict| 账户交易列表|

**交易详情**
| 字段名称 | 类型   | 说明                   |
| :------- | :----- | :--------------------- |
| blockNumber    | int    | 交易所在区块号 |
| source      | string |   交易from地址             |
| to      | string |   交易to地址               |
| hash | string | 交易哈希 |
| value | string | 交易value值 |
|time | string | 交易时间|
|fee | int | 交易花费 |
| confirmations | int | 最新出块确认,>0为否=0时为最新  |
| gasPrice     | int |   交易gas价格             |  
| gas      | int |   交易花费gas |


#### tm返回数据
tm无账户不支持此接口

### 返回数据示例
#### bsc返回数据示例

```json
{
    "code":200,
    "total_size":560,
    "page":1,
    "total_page":56,
    "return_data": [
         {
            "hash":"0xa2273891a95472a205dd4ce57c26abc34cef5807eba1d13229e4162ddc2d6f08",
            "gasPrice":0,
            "source":"0x38580efe497b22acc29783273e725a2a4f2aeea4",
            "value":"0x0",
            "to":"0x0000000000000000000000000000000000001001",
            "gas":9223372036854775807,
            "blockNumber":3948,
            "time":"2023-02-02 08:35:32",
            "fee":0,
            "confirmations":6049
        }
    ]
}
```
#### tm返回数据示例
tm无账户不支持此接口
