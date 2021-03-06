# Discord TTS bot「しゃべりな」
こちらはDiscordの読み上げbot「しゃべりな」のソースコードです．音声合成エンジンにはOpenJTalkを使用しています．  
botの招待は[こちら](https://bit.ly/invite-shaberina)（2022/2/16現在，参加サーバー数上限につき招待不可）  

![しゃべりな](https://user-images.githubusercontent.com/83697982/154113716-94acc059-e772-4c34-829f-b1ad1da3c05f.png)

# 目次
- [デモ動画](https://github.com/sabrina9561/shaberina/edit/master/README.md#%E3%83%87%E3%83%A2%E5%8B%95%E7%94%BB)
- [特徴](https://github.com/sabrina9561/shaberina/edit/master/README.md#%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89)
- [コマンド](https://github.com/sabrina9561/shaberina/edit/master/README.md#%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89)
- [開発環境](https://github.com/sabrina9561/shaberina/edit/master/README.md#%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83)
- [必要なもの](https://github.com/sabrina9561/shaberina/edit/master/README.md#%E5%BF%85%E8%A6%81%E3%81%AA%E3%82%82%E3%81%AE)
- [準備](https://github.com/sabrina9561/shaberina/edit/master/README.md#%E6%BA%96%E5%82%99)
- [実行方法](https://github.com/sabrina9561/shaberina/edit/master/README.md#%E5%AE%9F%E8%A1%8C%E6%96%B9%E6%B3%95)
- [その他](https://github.com/sabrina9561/shaberina/edit/master/README.md#%E3%83%A9%E3%82%A4%E3%82%BB%E3%83%B3%E3%82%B9%E7%AD%89)
- [ライセンス等](https://github.com/sabrina9561/shaberina/edit/master/README.md#%E3%81%9D%E3%81%AE%E4%BB%96)

# デモ動画
https://user-images.githubusercontent.com/83697982/154139889-170c2a1a-e81b-497a-9601-3baf9c4544c4.mp4

# 特徴
- 自動入退室に対応！コマンドを覚えなくても使い始められます
- ユーザーごとにボイスを設定！スピードやトーンはもちろん，話者やボイスエフェクトも変更できます
- サーバー設定が可能！自動入退室や入退室者名の読み上げなどを自由に設定できます

# コマンド
### 基本操作
`;join`：ボイスチャンネルに入室する．  
`;leave`：ボイスチャンネルから退室する．
### ボイス設定
`;voice`：現在のボイス設定を表示する．  
`;voice reset`：ボイス設定をリセットする．  
`;voice random`：ボイス設定をランダムに変更する．  
`;speaker ＿`：話者を＿に変更する．(mei, takumi)  
`;emotion ＿`：感情を＿に変更する．(normal, happy, angry, sad)  
`;effect ＿`：エフェクトを＿に変更する．(none, robot, whisper)  
`;tone ＿`：トーンを＿に変更する．(-5 ~ +5)  
`;speed ＿`：スピードを＿に変更する．(-5 ~ +5)
### サーバー設定
`;setting`：現在のサーバー設定を表示する．  
`;setting reset`：サーバー設定をリセットする．  
`;prefix ＿`：プレフィックスを＿に変更する．(任意の文字)  
`;target_ch ＿/all`：操作チャンネルを＿/allに変更する．(任意のテキストチャンネル)  
`;auto_join on/off`：自動入室を変更する．  
`;read_access on/off`：入退室読み上げを変更する．  
`;read_author on/off`：送信者名読み上げを変更する．  
`;read_outsider on/off`：非参加者読み上げを変更する．
### ヘルプ
`;help`：ヘルプを確認する．  
`;help voice`：ボイス設定の詳細ヘルプを確認する．  
`;help setting`：サーバー設定の詳細ヘルプを確認する．

# 開発環境
- 言語：Python3（python-3.9.7）
- 音声合成エンジン：OpenJtalk
- データベース：PostgreSQL
- インフラ：Heroku

# 必要なもの
- requirement.txtに記載のPythonライブラリ
- OpenJtalk
  - OpenJtalkの実行ファイル
  - 音響モデル（htsvoiceファイル）
  - 辞書（~.dic等）
- Discordのbotアカウントとそのトークン
- PostgreSQLデータベースのURL

# 準備
- Pythonライブラリは以下のコマンドでインストールできます．
```bash
pip install -r requirement.txt
```
- OpenJtalkファイル群の入手，botトークンの取得などについては解説サイトが数多く存在するのでそちらを参照してください．
- OpenJtalkファイル群をそれぞれopenjtalk/内の~.dummyと置き換えて配置してください．
- botトークンとPostgreSQLのURLをそれぞれ.env.dummy内の変数に入力し，ファイル名を.envに変更してください．

# 実行方法
以下のコマンドを実行することでbotが起動します．
```bash
python discordbot.py
```

# その他
当方では，大規模辞書「[NEologd](https://github.com/neologd/mecab-ipadic-neologd/blob/master/README.ja.md)」およびアクセント推定ソフト「[tdmelodic](https://github.com/PKSHATechnology-Research/tdmelodic)」を用いることで，
OpenJtalkに付属のものと比較して語彙数を大幅に増加させた辞書を作成し，botを運用しています．


# ライセンス等
「しゃべりな」のソースコードは配布を目的としたものではありません．利用は個人的な用途のみとしてください．

- Openjtalk：Modified BSD license
- 音響モデル（mei,takumi）：Creative Commons Attribution 3.0 license
- Neologd：Apache License 2.0
- tdmelodic：BSD 3-Clause License
- イラスト：ノーコピーライトガール
