# Git이란?

분산 버전 관리 시스템.

# Git을 사용하는 이유

## 버전 추적

![회의록 예시](https://velog.velcdn.com/images/sunkeydokey/post/07054d32-c834-41ac-88c3-925e5e982e5f/image.png)

> 위 파일은 무엇이 최종버전일까?
> 무엇이 바뀌었을까?

![Gitlog](https://velog.velcdn.com/images/sunkeydokey/post/6cfb0075-24e2-459f-bd59-940d7fbb0c20/image.png)

![Gitdiff](https://velog.velcdn.com/images/sunkeydokey/post/907fe16c-4325-4ce3-9aa3-257cedacec13/image.png)

Git 저장소는 파일의 내용이 다르면 다른 파일로 인식하여 commit마다 다른 시리얼을 부여한다. 이 덕분에 버전 추적을 통해 파일의 변동사항을 확인하고 혼선을 줄일 수 있다.

## 협업

![host push](https://velog.velcdn.com/images/sunkeydokey/post/46f3ae33-2b00-48d5-b8b5-b37a61db52ae/image.png)

![pull](https://velog.velcdn.com/images/sunkeydokey/post/bdc64ba3-6ef3-4f54-bdbd-1f39fbe67f42/image.png)

파일의 변경사항을 스냅샷 기반으로 추적해 프로젝트에서 여러 작업자 간의 작업을 조율할 수 있다. 원격저장소에 프로젝트 파일을 두고 Pull과 Push를 통해 자신의 로컬에서 파일을 수정하며 작업할 수 있다.

# 1. 설치

[git - Downloads](https://git-scm.com/downloads)에서 자신의 운영체제와 맞는 파일 설치한다.

# 2. git init

![folder](https://velog.velcdn.com/images/sunkeydokey/post/ec6e6e15-7122-4db5-a25c-856445d9f42d/image.png)

자신의 프로젝트를 관리할 저장소 폴더를 만들고 연다.

![gitbash](https://velog.velcdn.com/images/sunkeydokey/post/946ec7a7-b0a6-4405-b98e-b5d455155e9c/image.png)

해당 폴더에서 터미널을 동작할 수 있는 Git Bash, Powershell, VS Code 등을 실행한 후 git init을 입력한다.
`Initialized empty Git repository in '.....'` 메세지가 출력되었다면 git은 이제 이 폴더에서의 프로젝트 변동사항을 관리할 수 있다.

# 3. commit 해보기

이제부터는 VS Code를 활용하기로 한다.

## git status

![first.md](https://velog.velcdn.com/images/sunkeydokey/post/ea32d2ca-20c6-4dd3-81c1-bcfdfd61e898/image.png)

프로젝트의 첫 파일인 `first.md` 파일을 생성해보았다.

> VS Code를 사용하고 있다면 Ctrl + \`(백틱)를 통해 터미널을 열어보자.

![git status](https://velog.velcdn.com/images/sunkeydokey/post/f79543f5-c959-43e6-90c0-b708464cf12b/image.png)

터미널에서 `git status` 라는 명령어를 입력하면 현재 프로젝트 내부의 상태를 알 수 있다.

현재 상태를 보면 first.md 라는 파일 Untracked file 이고, commit을 위해 추가된 것이 없지만 untracked file이 존재한다는 메세지를 확인할 수 있다.

추가로 `git add <file>...` 명령어를 사용해 commit할 파일을 포함시킬 수 있다는 것도 알려준다.

## git add

![add.md](https://velog.velcdn.com/images/sunkeydokey/post/27213463-e3fa-4bca-a991-ddb8ca2918ca/image.png)

![git add](https://velog.velcdn.com/images/sunkeydokey/post/94f62d39-847a-4350-8388-b7f21cc8f74a/image.png)

![status after add](https://velog.velcdn.com/images/sunkeydokey/post/c5b14908-43fb-4c2d-b847-dcf6d6c1fe4d/image.png)

`add.md`라는 파일을 추가 생성한 후 안내된 메세지대로 git add 명령어를 통해 두 파일을 add해 주었다. 그 후 다시 git status를 활용하면 커밋될 변동사항 목록에 add.md와 first.md가 있는 것을 확인할 수 있다.

> 만약 변동사항이 있는 파일들을 한번에 add하고 싶다면 `git add .` 명령어를 사용하면 된다.

## Stage와 git rm

### Stage

![Stage](https://velog.velcdn.com/images/sunkeydokey/post/5778979f-7313-4a28-acd1-f9d3949a48f1/image.png)

git add 후에 status를 확인하면 unstage를 할 수 있는 `git rm` 명령어를 알려준다. git에는 stage 혹은 인덱스라는 개념이 있다. 프로젝트의 변동사항은 add와 동시에 커밋되는 것이 아닌 stage라는 가상의 대기장소에 놓여진다. stage에 대기하는 변동사항들을 하나의 새로운 버전으로 재출시하는 것이 commit이다.

### git rm

![git rm](https://velog.velcdn.com/images/sunkeydokey/post/69745fe1-42c1-4dff-acd4-00f22f53eebb/image.png)

add.md 파일은 커밋하고 싶지 않기 때문에 `git rm --cached add.md` 명령어를 입력해 stage에서 내려주었다. 이후 status를 확인하면 add.md 파일은 다시 untracked file이 되어 있다.

## git commit

![commit](https://velog.velcdn.com/images/sunkeydokey/post/b282db51-451d-4062-837a-91092ddc752a/image.png)

이제 commit을 해보도록 한다. `git commit` 명령어를 입력해보자.

![commit message](https://velog.velcdn.com/images/sunkeydokey/post/4994cfba-a61c-410f-95aa-2b90fcffd9de/image.png)

제발 commit 메세지를 입력해달라고 사정사정하는 모습이다. commit 메세지는 협업을 위해서 아주 중요하다. commit은 변동사항의 기록이기 때문에 팀 혹은 오픈소스 기여자가 함께 보는 코드에서 메세지를 통해 무엇을 왜 어떻게 변동시켰는지 추적이 되지 않는다면 후에 문제가 생겼을 때 치를 대가는 아주 크다. 따라서 팀 단위 이상으로 사용하는 저장소를 사용한다면 commit 메세지의 컨벤션을 따로 정해두는 것이 좋다.

그러니 중요한 commit은 메세지를 잘 남기기로 다짐하며 First commit 이라는 메세지와 함께 저장한 COMMIT_EDITMSG를 닫아준다.

> VS Code는 git관련 연동이 꽤나 잘 되어 있기 때문에 터미널 상에서 처리해야할 작업들을 유저 인터페이스에 띄워준다.
> 터미널에서 짧은 commit message를 한번에 작성할 목적이라면 `git commit -m "작성할 메세지"` 명령어를 입력하면 된다.

## git log

![git log](https://velog.velcdn.com/images/sunkeydokey/post/02dc4b6a-8f2b-491c-93d2-b1af1c06b7e9/image.png)

`git log` 명령어를 통해 commit 기록들을 살펴볼 수 있다. commit은 40글자의 영어, 수 조합의 고유이름 붙는다. 사실상 고유값이라 할 수 있어 겹칠 걱정은 하지 않아도 된다.

> commit 내역이 너무 많아 터미널에서 다 읽기 힘들다면 `git shortlog`를 통해 확인하는 방법도 있다.

## .gitignore

![.gitignore](https://velog.velcdn.com/images/sunkeydokey/post/f26338ed-715e-40d7-9c1b-122d22807a92/image.png)

변동 사항을 `git add .` 을 통해 한번에 추가하고 싶은데 수많은 파일 중 몇 개의 파일만 추가되지 않기를 원할 수 있다. 그럴 땐 프로젝트 폴더 내에 `.gitignore` 라는 파일을 생성한 후 절대 commit하고 싶지 않은 파일들의 파일명을 작성하면 된다.

![add.md mod](https://velog.velcdn.com/images/sunkeydokey/post/f2da4985-e1c7-4410-8a4b-20d5703a8c27/image.png)

![no add.md](https://velog.velcdn.com/images/sunkeydokey/post/88d10f45-c2b0-40f7-9ce5-baae118e3884/image.png)

rm으로 unstage된 add.md는 git status로 확인하면 붉은 글씨로 우리를 위협하였으나 .gitignore를 통해 얌전하게 제압하였다.

# GitHub 연동

GitHub는 가장 인기 있는 Git 저장소 호스팅 서비스이다. 로컬저장소인 현재 폴더와 GitHub 레포지토리를 연동해 원격저장소를 통해 내 프로젝트를 소싱하고, 다른 사람들과 작업을 공유할 수 있다. Gmail 계정이나 회원가입을 통해 계정을 만들어보자.

> GitHub 외의 선택지.
> 회사나 개인에 따라 Gitlab, bitbucket 등의 서비스를 사용할 수도 있다. [호스팅 서비스](https://git.wiki.kernel.org/index.php/GitHosting)들은 링크에서 확인 가능하다.

계정을 만들었다면 다시 VS Code 터미널에서

```Linux
git config --global user.name "GitHub 계정 이름"
git config --global user.email GitHub 계정 이메일
```

를 입력한다.

![연동](https://velog.velcdn.com/images/sunkeydokey/post/9f895a44-b579-444e-b2ff-8b03e8f1d644/image.png)

이후 아무 commit이나 추가한 후 git log를 보면 Author가 자신이 설정한 email과 name으로 바뀌어 있음을 알 수 있다.

# Repository 생성

![Repository](https://velog.velcdn.com/images/sunkeydokey/post/f8d0c271-01e7-448c-8470-a87d16ec4ea0/image.png)

내 프로젝트를 원격으로 저장해둘 공간이 필요하다. GitHub에서 Repositories 란을 누르고, New를 눌러보자.

![Create a Repository](https://velog.velcdn.com/images/sunkeydokey/post/5826c73b-1371-42ea-a7ae-702b27f10a2e/image.png)

- Name : 새 Repository를 생성하는 서식이 보이는데 Git-practice로 일단 해두었다. 자신의 프로젝트나 목적에 맞게 알아서 이름을 정하면 된다.
- Public or Private : Repository 공개 여부, 민감한 파일이라면 Private로 설정하면 된다.
- README : README.md 파일은 Description이외의 Repository의 설명 문서로, 프로젝트에 대한 설명 뿐만 아니라 사용방법, License 등을 기록한다.

![초기화면](https://velog.velcdn.com/images/sunkeydokey/post/ea285c16-a051-4794-9303-a9025c812754/image.png)

필요한 사항들을 입력한 후 Create repository 버튼을 누르면 다음과 같은 화면을 볼 수 있다. VS Code 터미널로 돌아와 `git remote add origin 저장소URL` 을 입력한다.

![remote-v](https://velog.velcdn.com/images/sunkeydokey/post/a3b5aad4-3f1e-497b-b073-f20ac23c31b4/image.png)

`git remote -v` 명령어를 입력하여 자신의 저장소 URL이 정상적으로 출력된다면 원격저장소와 자신의 로컬 폴더가 잘 연동된 것이다.

# 로컬파일을 원격저장소로 보내는 push

![push](https://velog.velcdn.com/images/sunkeydokey/post/2eb9c4e1-f419-4f17-97dc-4eb964d74112/image.png)

`git push 저장소명 브랜치명` 을 통해 내 로컬 저장소의 파일을 연동된 원격 저장소로 보낼 수 있다. 폴더가 원격저장소와 연동되면 origin이라는 명칭을 자동으로 가진다. 그리고 `git branch`를 통해 현재 브랜치가 main 이라는 것을 확인하였으니 `git push origin main` 을 통해 내가 지금까지 commit한 내역들을 원격저장소로 push할 수 있다.

![pushed](https://velog.velcdn.com/images/sunkeydokey/post/22f455ae-584c-4288-beac-e05bcbb59d6d/image.png)

내 GitHub 레포지토리에 정상적으로 first.md 파일이 push되었다.

# 원격저장소의 파일을 로컬 폴더로 데려오는 pull

같은 프로젝트를 진행하는 동료가 코드나 파일을 수정하고 원격저장소에 push를 했다고 생각해보자. 나는 그 사실을 모르고 내 컴퓨터로 파일을 수정하고 있다면? 동료가 수정한 내용을 카톡으로 매일매일 받아야 할까?

![동료의 수정](https://velog.velcdn.com/images/sunkeydokey/post/76aec892-dd06-4d2f-a714-c81bd6d47140/image.png)

이러한 상황을 재현하기 위해 (나는 협업할 친구가 없다.) 작업을 진행하고 있는 로컬 폴더가 아닌 GitHub에서 first.md파일을 수정해보았다.

![결과](https://velog.velcdn.com/images/sunkeydokey/post/e83f7b3d-1d59-460d-b590-70ae324c8e28/image.png)

그 결과 내 컴퓨터에서 작업하는 first.md 파일과 저장소의 first.md 파일은 다른 파일이 되어버렸다.

![nothing to commit](https://velog.velcdn.com/images/sunkeydokey/post/f38383a8-02c9-4d6d-b580-8182ca7f04e5/image.png)

나름 중요한 사안인데 git status로도 이 상황을 인지할 수 없다.

![로컬에서 수정](https://velog.velcdn.com/images/sunkeydokey/post/56add0e8-eab2-476e-a8b0-8332c923ffbc/image.png)

![수정 후 push](https://velog.velcdn.com/images/sunkeydokey/post/bab4e1da-2fba-4956-a43a-31d9cc624070/image.png)

같은 줄의 내용을 로컬에서 다른 내용을 작성하고 push를 하고 싶어도 거절을 당한다. 그래서 이런 경우에 pull을 통해 원격저장소의 현재 버전에 맞게 내 로컬의 버전을 맞추는 것이 필요하다.

`git pull origin main` 명령어를 입력해보자.

![pull conflict](https://velog.velcdn.com/images/sunkeydokey/post/bf46180f-d32e-4833-9dd5-3eb3ad67c6c5/image.png)

서로 같은 부분을 수정했으니 충돌이 일어났다. Accept Both Changes를 눌러 두 commit 모두 받아들여보기로 한다. 그 후 commit과 push를 하면

![pull & push](https://velog.velcdn.com/images/sunkeydokey/post/0b17ad65-8bfb-4cf8-bb23-f11a977a8bb5/image.png)

동료와 나의 수정사항이 모두 반영된 first.md가 원격저장소에 저장된다.
