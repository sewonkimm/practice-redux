# Redux 배우기

> [공식문서 읽기](https://ko.redux.js.org/)
## React Redux 앱 만들기

```bash
npx create-react-app my-app --template redux
```

CRA를 위한 공식 Redux+JS 템플릿을 사용하면 RTK(Redux Toolkit)을 사용할 수 있는 redux 앱이 만들어진다.
이미 있는 프로젝트에 RTK를 설치해야한다면 `npm install @reduxjs/toolkit` 명령어로 패키지를 받아 사용해야한다.

## Project 시작하기

```bash
yarn start
```

## Redux 기본 개념

1. Store : state가 저장되어 있는 단 하나의 공간
2. Action : Store의 상태를 변경할 수 있는 단 한가지 방법
3. Reducer : Action이 어떻게 Store를 변경할 것인지 명시한 것. 우리가 작성해야할 부분

### Store

- 보통 하나의 Store에서 하나의 root reducer 함수를 가지는 형태.
- 앱이 커지면 root reducer를 작은 reducer로 나눌 수 있음.
- `getState()` 함수로 state에 접근. selector 패턴을 사용하면 필요한 state만 가져와 효율성 증가.
- `dispatch()` 함수로 store를 갱신. 인자로 action을 넘겨줌. dispatch를 event trigger라고 생각해도 무방.
- 


### Action 

```javascript
store.dispatch({ type: 'ACTION' })

// action 예제 
const addAction = {
    type: 'todos/todoAdded',
    payload: 'Study Redux'
}

// action creator 예제
const addTodo = text => {
    return {
        type: 'todos/todoAdded',
        payload: 'Study Redux'
    }
}
```

- action은 type 필드를 가진 js object
- action object가 가진 추가 정보는 payload라고 부름
- action creator는 action object를 반환하는 함수
- 

### Reducer⭐

```javascript
(state, action) => newState

// 예제
const initialState = { value: 0 }

function counterReducer(state = initialState, action) {
  if (action.type === 'counter/increment') {
    return {
      ...state,
      value: state.value + 1
    }
  }
  return state
}
```

- Array.reduce() 함수에서 유래한 명칭
- 반드시 현재 state 값을 기반으로 **immutable update**를 해야함
- async login, random한 value 계산 등을 허용하지 않음
