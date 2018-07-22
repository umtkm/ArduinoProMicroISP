
# Arduino Pro Micro ISP

Arduino Pro Micro (ATmega32u4搭載)で他のArduinoにISPで書き込むためのプログラムです．ArduinoのExamplesのArduino ISPを改変しました．

## 使い方(簡易版)

簡潔に使い方をまとめておきます．詳しい説明は後ほど公開します．

### Pro Micro をISP化

1. このリポジトリをclone/downloadし，"ArduinoProMicroISP.ino"をArduino IDEで開く
1. [Tools] > [Board:] で Arduino Leonardo を選択
1. [Tools] > [Port:] で Pro Micro が接続されたポートを選択
1. [Sketch] > [Upload] で，通常のプログラムの書き込みと同じように書き込む

### 他の Arduino に書き込む

1. ターゲットのICSP端子と Pro Micro を結線する(SPIのピン番号はコード内の記述を参照)
1. Pro Micro の 8番ピンと9番ピンをジャンパピン等で短絡させる
1. [Tools] > [Board:] でターゲットのArduinoを選択
1. [Tools] > [Port:] は ** Pro Micro が接続されたポート ** のままにしておく
1. [Tools] > [Programmer:] で"Arduino as ISP"を選択
1. [Sketch] > ** [Upload Using Programmer] ** で書き込む

### シリアル通信バイパス機能

ターゲットとPC間のシリアル通信をバイパスさせることが可能です．デフォルトの Baudrate は 115200 bps です．

1. ターゲットのTXを Pro Micro のRXに接続する
1. 同様に，ターゲットのRXを Pro Micro のTXに接続する
1. 8番ピンと9番ピンのジャンパピンを取り除き，8番ピンを開放
1. シリアルモニタで通常通り通信する．この時，Baudrateは固定なので注意．


## ピン番号やBaudrateの変更

ピン番号やBaudrateは基本的にプリプロセッサマクロで定義しています．変更する場合はコードを見て適宜変更してください．