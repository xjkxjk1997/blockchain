
# 期末项目报告
## 16340254 谢济锴

## 1.Github链接
[PORTAL]()
## 2.选题背景、依据
基于区块链的投票应用即用户可以在不可信的分布环境中对特定候选人投票，每次投票都会被记录在区块链上。可以实现管理层对每个用户根据其用户类别赋予其不同的投票权重，统计用户的总数，和有效的投票数，判断此次投票是否有效是否生效等功能。投票直接在链上进行统计并且公布，根据区块链的特性，干扰投票的过程和篡改投票的结果会变得非常困难。由此，该应用不失为一个高效安全的投票方式。
基本规则为投票人每人只有一票且候选人不能参与投票，候选人票数多获胜。选取这个题目原因一是因为集体决策尤其是投票机制是以太坊乃至整个区块链应用的一个核心的价值主张。另一个原因在于，投票是很多复杂的去中心化应用的基础构件，许多的应用都是以投票为雏形进行拓展和变化的。
对于现有的教务系统评教、选课等功能，以此作为基础，可以制作新版本的教务系统。评教方面：信息投放匿名，且可以供所有参与者查看，让评教更加客观真实。选课方面：由教师开放课程（需要管理员通过审理），学生进行选课（随机选，抢选）。

## 3.使用说明

### 环境
本次项目使用虚拟机环境作为以太坊节点，在 Windows 下完成编写和测试。
- OS: Ubuntu 16.04 LTS server
- node: v4.4.2
- npm: 6.4.1
- web3js: web3@0.20.7
- testRPC: EthereumJS TestRPC v6.0.3 (ganache-core: 2.0.2)
- Truffle: Truffle v4.1.14

### 文件
- Ballot.sol 智能合约源码
- Ballot_index.html 前端界面
- main.css css样式表
- deploy.pdf 部署报告

### 部署
区块链部署详细内容参照部署报告（源码有修改内容，部分函数及参数发生了变化，但合约的部署方式不变）
application部署
在Remix上0.4.22以上版本的编译器，部署至web3 provider上

### UI介绍
![ui1](./intro1.png)
![ui2](./intro2.png)

## 4.测试

### tuffle test(linux虚拟环境下)

```
sudo apt install curl
curl -sL https://deb.nodesource.com/setup_8.x | sudo bash -
sudo apt install nodejs

node -v # failed
npm -v

sudo ln -s /usr/bin/nodejs /usr/bin/node
node -v # pass

sudo npm install -g truffle

mkdir bc
cd bc
truffle unbox metacoin
```

![test1](./test1.png)  
默认创建了候选人'Trump'，在UI界面点击Add后，在geth中调用函数进行查看结果如下
```
var account_one = web3.eth.accounts[0];
var candidateNum = Ballot.getNumOfCandidates()；
console.log("Total num of candidates: ", candidateNum.toNumber());
2
```

![test2](./test2.png)  
在UI界面点击Vote后，在geth中调用函数进行查看结果如下
```
var account_one = web3.eth.accounts[0];
var voteNum = Ballot.totalVotes(1)；
console.log("Total votes of candidate 1: ", voteNum.toNumber());
1
```
