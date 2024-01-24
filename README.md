## CSEncryptType

Enrypted data types for Unity games to defend against memory cheat tools, which could search the memory of critical datas and change their values. Use the encrypted types other than built-in data types for critical datas such as player blood, the number of coins, etc.

### Features

The encrypted types supported:

- EncryptByte
- EncryptSByte
- EncryptShort
- EncryptUShort
- EncryptInt
- EncryptUInt
- EncryptLong
- EncryptULong
- EncryptFloat
- EncryptDouble

Just replace the existing built-in data types with them. No code needs to change, since the type conversion operators will handle the work.

---

## CSEncryptType

用于Unity游戏项目的加密数据类型，可防御常见的内存破解/外挂工具，比如八门神器，葫芦侠，烧饼修改器等。常用于加密游戏中的关键数据类型，比如玩家血量，金币数量等

### Features

支持的加密类型:

- EncryptByte
- EncryptSByte
- EncryptShort
- EncryptUShort
- EncryptInt
- EncryptUInt
- EncryptLong
- EncryptULong
- EncryptFloat
- EncryptDouble

只需要把项目中已有的内置数据类型替换为加密类型。不需要改其他代码，类型转换操作符会处理剩下的事情

## 说明

该代码实现的要点：

1 用泛型尽量精简了代码。

2 实现了类型转换的操作符，这样能最大程度简化已有项目的重构，比如若要将基础数据类型更改为加密数据类型，只需要更改变量声明处的类型，比如将int改为EncryptInt，其他的上层代码不需要做任何改动，自定义的类型转换操作符会帮助编译器处理剩下的工作。

需要注意的是，实际项目中应全面地对任何游戏界面可见的关键性数据做加密，比如金币，血量，攻击力等。而且，所有会和关键性数据做运算的相关数据，也得用加密类型。比如，有一个游戏内弹框界面，上面可以让玩家自由选择要购买的道具数量及对应的金币花费，那么此处的金币花费的变量也应做加密。否则，玩家通过多次更改道具数量，就能用工具很容易地搜索出金币花费对应的地址，然后将其修改为0或者负数，再进行购买，就能达到买道具不花钱或者买完金币增加的效果。防破解这种事，百密一疏就会导致严重的问题，所以在防御上要尽量考虑全面。
